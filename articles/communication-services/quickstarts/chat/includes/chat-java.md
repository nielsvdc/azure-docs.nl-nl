---
title: bestand opnemen
description: bestand opnemen
services: azure-communication-services
author: mikben
manager: mikben
ms.service: azure-communication-services
ms.subservice: azure-communication-services
ms.date: 9/1/2020
ms.topic: include
ms.custom: include file
ms.author: mikben
ms.openlocfilehash: 1675ad802f3a117c26ee10218f3b3bedad9b0a00
ms.sourcegitcommit: ef69245ca06aa16775d4232b790b142b53a0c248
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/06/2020
ms.locfileid: "91779820"
---
## <a name="prerequisites"></a>Vereisten

- Een Azure-account met een actief abonnement. [Gratis een account maken](https://azure.microsoft.com/free/?WT.mc_id=A261C142F)
- [Java Development Kit (JDK)](https://docs.microsoft.com/java/azure/jdk/?view=azure-java-stable&preserve-view=true) versie 8 of hoger.
- [Apache Maven](https://maven.apache.org/download.cgi).
- Een actieve Communication Services-resource en verbindingsreeks. [Een Communication Services-resource maken](../../create-communication-resource.md).
- Een[Toegangstoken voor gebruikers](../../access-tokens.md). Zorg ervoor dat u het bereik instelt op “chat“ en noteer de tokenreeks en ook de gebruikersId-reeks.


## <a name="setting-up"></a>Instellen

### <a name="create-a-new-java-application"></a>Een nieuwe Java-toepassing maken

Open uw terminal- of opdrachtvenster en navigeer naar de map waarin u uw Java-toepassing wilt maken. Voer de onderstaande opdracht uit om het Java-project te genereren op basis van de maven-archetype-snelstart-sjabloon.

```console
mvn archetype:generate -DgroupId=com.communication.quickstart -DartifactId=communication-quickstart -DarchetypeArtifactId=maven-archetype-quickstart -DarchetypeVersion=1.4 -DinteractiveMode=false
```

U ziet dat het doel 'genereren' een map heeft gemaakt met dezelfde naam als de artifactId. De `src/main/java directory` in deze map bevat de broncode van het project, de map `src/test/java` bevat de testbron en het bestand pom.xml is het Project Object Model van het project of [POM](https://maven.apache.org/guides/introduction/introduction-to-the-pom.html).

Het POM-bestand van uw toepassing bijwerken voor het gebruik van Java 8 of hoger:

```xml
<properties>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    <maven.compiler.source>1.8</maven.compiler.source>
    <maven.compiler.target>1.8</maven.compiler.target>
</properties>
```

### <a name="add-the-package-references-for-the-chat-client-library"></a>De pakketreferenties voor de chat-clientbibliotheek toevoegen

In uw POM-bestand verwijzen we naar het pakket `azure-communication-chat` met de chat-API's:

```xml
<dependency>
    <groupId>com.azure</groupId>
    <artifactId>azure-communication-chat</artifactId>
    <version>1.0.0-beta.2</version> 
</dependency>
```

Voor verificatie moet uw client het pakket `azure-communication-common` verwijzen :

```xml
<dependency>
    <groupId>com.azure</groupId>
    <artifactId>azure-communication-common</artifactId>
    <version>1.0.0-beta.2</version> 
</dependency>

```

## <a name="object-model"></a>Objectmodel

De volgende klassen en interfaces verwerken enkele van de belangrijkste functies van de Azure Communication Services chat-clientbibliotheek voor Java

| Naam                                  | Beschrijving                                                  |
| ------------------------------------- | ------------------------------------------------------------ |
| ChatClient | Deze klasse is vereist voor de chat-functionaliteit. U instantieert deze klasse met uw abonnementsgegevens en gebruikt deze om threads te maken, krijgen en verzenden. |
| ChatAsyncClient | Deze klasse is vereist voor de asynchrone chat-functionaliteit. U instantieert deze klasse met uw abonnementsgegevens en gebruikt deze om threads te maken, krijgen en verzenden. |
| ChatThreadClient | Deze klasse is vereist voor de functionaliteit van de chat-thread. U verkrijgt een instantie via de ChatClient en gebruikt deze om berichten te verzenden/ontvangen/bijwerken/verwijderen, gebruikers toe te voegen/te verwijderen of te verzenden, getypte meldingen te verzenden en bevestigingen te lezen. |
| ChatThreadAsyncClient | Deze klasse is vereist voor de functionaliteit van de asynchrone chat-thread. U verkrijgt een instantie via de ChatAsyncClient en gebruikt deze om berichten te verzenden/ontvangen/bijwerken/verwijderen, gebruikers toe te voegen/te verwijderen of te verzenden, getypte meldingen te verzenden en bevestigingen te lezen. |

## <a name="create-a-chat-client"></a>Een chat-client maken
Als u een chat-client wilt maken, gebruikt u het Communications Service-eindpunt en het toegangstoken dat is gegenereerd als onderdeel van de vereiste stappen. Met toegangstokens voor gebruikers kunt u clienttoepassingen maken die zich rechtstreeks verifiëren bij Azure Communication Services. Zodra u deze tokens op uw server hebt gegenereerd, geeft u ze terug op een clientapparaat. U moet de klasse CommunicationUserCredential van de gemeenschappelijke clientbibliotheek gebruiken om het token door te geven aan uw chat-client. 

Bij het toevoegen van de importinstructies, moet u ervoor zorgen dat u alleen importbewerkingen toevoegt vanuit de com.azure.communication.chat en com.azure.communication.chat.models naamspaties en niet vanuit de com.azure.communication.chat.implementation naamspatie. In het bestand App.java dat is gegenereerd via Maven, kunt u de volgende code gebruiken om te beginnen met:

```Java
import com.azure.communication.chat.*;
import com.azure.communication.chat.models.*;
import com.azure.communication.common.*;
import com.azure.core.http.HttpClient;

import java.io.*;

public class App
{
    public static void main( String[] args ) throws IOException
    {
        System.out.println("Azure Communication Services - Chat Quickstart");
        
        // Your unique Azure Communication service endpoint
        String endpoint = "https://<RESOURCE_NAME>.communication.azure.com";

        // Create an HttpClient builder of your choice and customize it
        // Use com.azure.core.http.netty.NettyAsyncHttpClientBuilder if that suits your needs
        NettyAsyncHttpClientBuilder yourHttpClientBuilder = new NettyAsyncHttpClientBuilder();
        HttpClient httpClient = yourHttpClientBuilder.build();

        // User access token fetched from your trusted service
        String userAccessToken = "<USER_ACCESS_TOKEN>";

        // Create a CommunicationUserCredential with the given access token, which is only valid until the token is valid
        CommunicationUserCredential userCredential = new CommunicationUserCredential(userAccessToken);

        // Initialize the chat client
        final ChatClientBuilder builder = new ChatClientBuilder();
        builder.endpoint(endpoint)
            .credential(userCredential)
            .httpClient(httpClient);
        ChatClient chatClient = builder.buildClient();
    }
}
```


## <a name="start-a-chat-thread"></a>Een chat-thread starten

De methode `createChatThread` gebruiken om een chat-thread te maken.
`createChatThreadOptions` wordt gebruikt om de thread-aanvraag te beschrijven.

- Gebruik `topic` om een onderwerp te geven aan deze chat. Het onderwerp kan worden bijgewerkt nadat de chat-thread is gemaakt met behulp van de functie `UpdateThread` .
- Gebruik `members` om de thread-leden weer te geven die aan de thread moeten worden toegevoegd. `ChatThreadMember` neemt u de gebruiker die u hebt gemaakt in de Snelstart [Toegangstoken voor gebruikers](../../access-tokens.md).

Het antwoord `chatThreadClient` wordt gebruikt om bewerkingen uit te voeren op de gemaakte chat-thread: leden toevoegen aan de chat-thread, een bericht verzenden, een bericht verwijderen, enz. Het bevat een eigenschap `chatThreadId` die de unieke ID van de chat-thread is. De eigenschap is toegankelijk via de openbare methode .getChatThreadId().

```Java
List<ChatThreadMember> members = new ArrayList<ChatThreadMember>();

ChatThreadMember firstThreadMember = new ChatThreadMember()
    .setUser(firstUser)
    .setDisplayName("Member Display Name 1");
    
ChatThreadMember secondThreadMember = new ChatThreadMember()
    .setUser(secondUser)
    .setDisplayName("Member Display Name 2");

members.add(firstThreadMember);
members.add(secondThreadMember);

CreateChatThreadOptions createChatThreadOptions = new CreateChatThreadOptions()
    .setTopic("Topic")
    .setMembers(members);
ChatThreadClient chatThreadClient = chatClient.createChatThread(createChatThreadOptions);
String chatThreadId = chatThreadClient.getChatThreadId();
```

## <a name="send-a-message-to-a-chat-thread"></a>Een bericht verzenden naar een chat-thread

Gebruik de methode `sendMessage` om een bericht te verzenden naar de thread die u zojuist hebt gemaakt, geïdentificeerd door chatThreadId.
`sendChatMessageOptions` wordt gebruikt om de aanvraag voor het chatbericht te beschrijven.

- Gebruik `content` om de inhoud van het chatbericht te geven.
- Gebruik `priority` om het prioriteitsniveau van het chatbericht te geven, zoals “Normaal“ of “Hoog“. Deze eigenschap kan worden gebruikt om een UI-indicator te hebben voor de ontvangende gebruiker in uw app, om de aandacht te vestigen op het bericht of om aangepaste bedrijfslogica uit te voeren.
- Gebruik `senderDisplayName` om de weergavenaam van de afzender te geven.

Het antwoord `sendChatMessageResult` bevat een `id`, dit is de unieke ID van het bericht.

```Java
SendChatMessageOptions sendChatMessageOptions = new SendChatMessageOptions()
    .setContent("Message content")
    .setPriority(ChatMessagePriority.NORMAL)
    .setSenderDisplayName("Sender Display Name");

SendChatMessageResult sendChatMessageResult = chatThreadClient.sendMessage(sendChatMessageOptions);
String chatMessageId = sendChatMessageResult.getId();
```


## <a name="get-a-chat-thread-client"></a>Een chat-thread-client ophalen

De methode `getChatThreadClient` retourneert een thread-client voor een thread die al bestaat. Het kan worden gebruikt voor het uitvoeren van bewerkingen op de gemaakte thread: leden toevoegen, bericht verzenden, enz. `chatThreadId` is de unieke ID van de bestaande chat-thread.

```Java
String chatThreadId = "Id";
ChatThread chatThread = chatClient.getChatThread(chatThreadId);
```

## <a name="receive-chat-messages-from-a-chat-thread"></a>Chatberichten ontvangen van een chat-thread

U kunt chatberichten ophalen door de methode `listMessages` op de chat-thread-client op bepaalde intervallen te pollen.

```Java
chatThreadClient.listMessages().iterableByPage().forEach(resp -> {
    System.out.printf("Response headers are %s. Url %s  and status code %d %n", resp.getHeaders(),
        resp.getRequest().getUrl(), resp.getStatusCode());
    resp.getItems().forEach(message -> {
        System.out.printf("Message id is %s.", message.getId());
    });
});
```

`listMessages` retourneert de meest recente versie van het bericht, inclusief eventuele bewerkingen of verwijderingen die zijn opgetreden in het bericht met behulp van .editMessage() en .deleteMessage(). Voor verwijderde berichten retourneert `chatMessage.getDeletedOn()` een datum/tijd-waarde die aangeeft wanneer dat bericht is verwijderd. Voor bewerkte berichten retourneert `chatMessage.getEditedOn()` een datum/tijd die aangeeft wanneer het bericht is bewerkt. De oorspronkelijke tijd van het maken van het bericht kan worden geopend met `chatMessage.getCreatedOn()` en kan worden gebruikt voor het bestellen van de berichten.

`listMessages` retourneert verschillende typen berichten die kunnen worden geïdentificeerd door `chatMessage.getType()`. Deze typen zijn:

- `Text`: Normaal chatbericht verzonden door een thread-lid.

- `ThreadActivity/TopicUpdate`: Systeembericht dat aangeeft dat het onderwerp is bijgewerkt.

- `ThreadActivity/AddMember`: Systeembericht dat aangeeft dat een of meer leden zijn toegevoegd aan de chat-thread.

- `ThreadActivity/DeleteMember`: Een systeembericht dat aangeeft dat een lid is verwijderd uit de chat-thread.

Zie [Berichttypen](../../../concepts/chat/concepts.md#message-types)voor meer informatie.

## <a name="add-a-user-as-member-to-the-chat-thread"></a>Een gebruiker toevoegen als lid van de chat-thread

Zodra u een chat-thread hebt gemaakt, kunt u gebruikers toevoegen en verwijderen. Door gebruikers toe te voegen, kunt u ze toegang geven tot het verzenden van berichten naar de chat-thread, en andere leden toevoegen/verwijderen. U moet beginnen met het ophalen van een nieuw toegangstoken en een nieuwe identiteit voor die gebruiker. Voordat u de methode addMembers aanroept, moet u ervoor zorgen dat u een nieuw toegangstoken en een nieuwe identiteit hebt verkregen voor die gebruiker. De gebruiker heeft het toegangstoken nodig om hun chat-client te initialiseren.

Gebruik methode `addMembers` om thread-leden toe te voegen aan de thread die wordt geïdentificeerd door threadId.

- Gebruik `members` om de leden weer te geven die moeten worden toegevoegd aan de chat-thread.
- `user`, vereist, is de CommunicationUser die u hebt gemaakt door de CommunicationIdentityClient in de Snelstart [Toegangstoken voor gebruikers](../../access-tokens.md).
- `display_name`, optioneel, is de weergavenaam voor het thread-lid
- `share_history_time`, optioneel, is de tijd van waaruit de chat-geschiedenis wordt gedeeld met het lid. Als u de geschiedenis wilt delen sinds het begin van de chat-thread, stelt u deze eigenschap in op een willekeurige datum die gelijk is aan of kleiner is dan de aanmaaktijd van de thread. Als u geen geschiedenis wilt delen voordat het lid is toegevoegd, stel het dan op de huidige datum in. Als u gedeeltelijke geschiedenis wilt delen, stelt u deze in op de vereiste datum.

```Java
List<ChatThreadMember> members = new ArrayList<ChatThreadMember>();

ChatThreadMember firstThreadMember = new ChatThreadMember()
    .setUser(user1)
    .setDisplayName("Display Name 1");

ChatThreadMember secondThreadMember = new ChatThreadMember()
    .setUser(user2)
    .setDisplayName("Display Name 2");

members.add(firstThreadMember);
members.add(secondThreadMember);

AddChatThreadMembersOptions addChatThreadMembersOptions = new AddChatThreadMembersOptions()
    .setMembers(members);
chatThreadClient.addMembers(addChatThreadMembersOptions);
```

## <a name="remove-user-from-a-chat-thread"></a>Gebruiker verwijderen uit een chat-thread

Net als bij het toevoegen van een gebruiker aan een thread, kunt u gebruikers uit een chat-thread verwijderen. Hiervoor moet u de gebruikersidentiteiten bijhouden van de leden die u hebt toegevoegd.

Gebruik `removeMember`, waarbij `user` de CommunicationUser is die u hebt gemaakt.

```Java
chatThreadClient.removeMember(user);
```

## <a name="run-the-code"></a>De code uitvoeren

Navigeer naar de map die het bestand *pom.xml* bevat en compileer het project met behulp van de volgende `mvn`-opdracht.

```console
mvn compile
```

Bouw vervolgens het pakket.

```console
mvn package
```

Voer de volgende `mvn`-opdracht uit om de app uit te voeren.

```console
mvn exec:java -Dexec.mainClass="com.communication.quickstart.App" -Dexec.cleanupDaemonThreads=false
```
