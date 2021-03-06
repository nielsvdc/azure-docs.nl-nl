---
title: Prestaties van VM-grootte van HB-serie
description: Meer informatie over prestatie test resultaten voor VM-grootten van de HB-serie in Azure.
author: vermagit
ms.service: virtual-machines
ms.topic: article
ms.date: 09/09/2020
ms.author: amverma
ms.reviewer: cynthn
ms.openlocfilehash: 2267dc23e2f886d87342fc22c3b12a03e8df6a86
ms.sourcegitcommit: 83610f637914f09d2a87b98ae7a6ae92122a02f1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "91994845"
---
# <a name="hb-series-virtual-machine-sizes"></a>Grootte van virtuele machines uit de HB-serie

Er zijn verschillende prestatie tests uitgevoerd op HB-serie-grootten. Hier volgen enkele van de resultaten van deze prestatie tests.

| Workload                                        | HB                    |
|-------------------------------------------------|-----------------------|
| Triad STREAMen                                    | 260 GB/s (32-33 GB/s per CCX)  |
| High-Performance Linpackuitvoer (HPL)                  | 1.000 GigaFLOPS (Rpeak), 860 GigaFLOPS (Rmax) |
| Band breedte & RDMA-latentie                        | 1,27 micro seconden, 99,1 GB/s   |
| FIO op lokale NVMe-SSD                           | 1,7 GB/s Lees bewerkingen, 1,0 GB/s      |  
| IOR op 4 * Azure Premium-SSD (P30 Managed Disks, RAID0) * *  | 725 MB/s Lees bewerkingen, 780 MB/schrijf bewerkingen   |


## <a name="mpi-latency"></a>MPI-latentie

MPI-latentie test van de OSU microbench Mark-suite wordt uitgevoerd. Voorbeeld scripts bevinden zich op [github](https://github.com/Azure/azhpc-images/blob/04ddb645314a6b2b02e9edb1ea52f079241f1297/tests/run-tests.sh)

```bash
./bin/mpirun_rsh -np 2 -hostfile ~/hostfile MV2_CPU_MAPPING=[INSERT CORE #] ./osu_latency 
```

:::image type="content" source="./media/latency-hb.png" alt-text="MPI-latentie op Azure HB.":::

## <a name="mpi-bandwidth"></a>MPI-band breedte

De MPI-bandbreedte test van de OSU microbench Mark-suite wordt uitgevoerd. Voorbeeld scripts bevinden zich op [github](https://github.com/Azure/azhpc-images/blob/04ddb645314a6b2b02e9edb1ea52f079241f1297/tests/run-tests.sh)

```bash
./mvapich2-2.3.install/bin/mpirun_rsh -np 2 -hostfile ~/hostfile MV2_CPU_MAPPING=[INSERT CORE #] ./mvapich2-2.3/osu_benchmarks/mpi/pt2pt/osu_bw
```

:::image type="content" source="./media/bandwidth-hb.png" alt-text="MPI-latentie op Azure HB.":::


## <a name="mellanox-perftest"></a>Mellanox perftest

Het [Mellanox perftest-pakket](https://community.mellanox.com/s/article/perftest-package) heeft veel InfiniBand-tests zoals latentie (ib_send_lat) en band breedte (ib_send_bw). Hieronder vindt u een voor beeld van een opdracht.

```console
numactl --physcpubind=[INSERT CORE #]  ib_send_lat -a
```

## <a name="next-steps"></a>Volgende stappen

- Meer informatie over de meest recente aankondigingen en enkele HPC-voor beelden (High Performance Computing) en resultaten van de [Azure Compute tech-community blogs](https://techcommunity.microsoft.com/t5/azure-compute/bg-p/AzureCompute).
- Zie [High Performance Computing (HPC) in azure](/azure/architecture/topics/high-performance-computing/)voor een architectuur weergave op een hoger niveau voor het uitvoeren van HPC-workloads.
