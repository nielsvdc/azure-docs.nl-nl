---
title: Lockup CPU-fout met watchdog-fouten van Azure HDInsight-cluster
description: Er wordt een tijdelijke Lockup-CPU voor een watchdog-fout weer gegeven in kernel syslogs van Azure HDInsight-cluster
ms.service: hdinsight
ms.topic: troubleshooting
author: hrasheed-msft
ms.author: hrasheed
ms.reviewer: jasonh
ms.date: 08/05/2019
ms.openlocfilehash: 33990e40507f088962fd8d8efd241de5d2fcc63b
ms.sourcegitcommit: 7863fcea618b0342b7c91ae345aa099114205b03
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/03/2020
ms.locfileid: "93289065"
---
# <a name="scenario-watchdog-bug-soft-lockup---cpu-error-from-an-azure-hdinsight-cluster"></a>Scenario: fout ' watchdog: BUG: zacht Lockup-CPU ' van een Azure HDInsight-cluster

In dit artikel worden de stappen beschreven voor het oplossen van problemen en mogelijke oplossingen voor problemen bij het werken met Azure HDInsight-clusters.

## <a name="issue"></a>Probleem

De kernel-syslogs bevatten het volgende fout bericht: `watchdog: BUG: soft lockup - CPU` .

## <a name="cause"></a>Oorzaak

Een [fout](https://bugzilla.kernel.org/show_bug.cgi?id=199437) in de Linux-kernel veroorzaakt CPU-Soft-Lockups.

## <a name="resolution"></a>Oplossing

Kernel-patch Toep assen. In het onderstaande script wordt de Linux-kernel bijgewerkt en worden de machines op verschillende tijdstippen in 24 uur opnieuw opgestart. Voer de script actie uit in twee batches. De eerste batch bevindt zich op alle knoop punten, behalve het hoofd knooppunt. De tweede batch bevindt zich op het hoofd knooppunt. Voer niet op het hoofd knooppunt en andere knoop punten tegelijk uit.

1. Ga vanuit Azure Portal naar uw HDInsight-cluster.

1. Ga naar script acties.

1. Selecteer **nieuwe verzenden** en voer de invoer als volgt in

    | Eigenschap | Waarde |
    | --- | --- |
    | Scripttype | -Aangepast |
    | Naam |Oplossing voor een probleem met de kernel-zachte vergrendeling |
    | Bash-script-URI |`https://raw.githubusercontent.com/hdinsight/hdinsight.github.io/master/ClusterCRUD/KernelSoftLockFix/scripts/KernelSoftLockIssue_FixAndReboot.sh` |
    | Knooppunttype(n) |Werk nemer, Zookeeper |
    | Parameters |N.v.t. |

    Selecteer **Deze script actie persistent maken...** als u het script wilt uitvoeren wanneer er nieuwe knoop punten worden toegevoegd.

1. Selecteer **Maken**.

1. Wacht totdat de uitvoering is geslaagd.

1. Voer de script actie uit op het hoofd knooppunt door dezelfde stappen te volgen als stap 3, maar deze keer met knooppunt typen: Head.

1. Wacht totdat de uitvoering is geslaagd.

## <a name="next-steps"></a>Volgende stappen

[!INCLUDE [troubleshooting next steps](../../../includes/hdinsight-troubleshooting-next-steps.md)]