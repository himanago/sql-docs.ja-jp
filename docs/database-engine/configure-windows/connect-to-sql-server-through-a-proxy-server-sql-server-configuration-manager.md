---
title: "プロキシ サーバーで SQL Server に接続する - SQL Server 構成マネージャー | Microsoft Docs"
ms.custom: 
ms.date: 12/15/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Remote WinSock
- RWS
- LATs
- proxy servers [SQL Server]
- connections [SQL Server], proxy server
- Microsoft Proxy Server [SQL Server]
- local address tables [SQL Server]
ms.assetid: 39714de0-2a1f-4179-9091-5c3fa4612545
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ccbdfcf1e8a313f87b80f7a10d027ee6c1e68ca1
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="connect-to-sql-server-through-a-proxy-server-sql-server-configuration-manager"></a>プロキシ サーバーを介して SQL Server に接続する方法 (SQL Server 構成マネージャー)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  このトピックでは、SQL Server 構成マネージャーを使用して、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] でプロキシ サーバーを介して SQL Server に接続する方法について説明します。 リモート WinSock (RWS) 経由でリモートで受信待ちするには、受信待ちするノード アドレスがローカル アドレス テーブル (LAT) のエントリの範囲外になるように、プロキシ サーバーに対して LAT を定義します。  
  
##  <a name="SSMSProcedure"></a> SQL Server 構成マネージャーの使用  
  
#### <a name="to-enable-connections-to-sql-server-through-microsoft-proxy-server"></a>Microsoft Proxy Server を介して SQL Server に接続できるようにするには  
  
1.  「[特定の TCP ポートで受信待ちするようにサーバーを構成する方法 &#40;SQL Server 構成マネージャー&#41;](../../database-engine/configure-windows/configure-a-server-to-listen-on-a-specific-tcp-port.md)」の手順に従い、[!INCLUDE[ssDE](../../includes/ssde-md.md)] で使用される TCP/IP ポートを判断するか、任意のポートを使用するように [!INCLUDE[ssDE](../../includes/ssde-md.md)] を構成します。  
  
2.  プロキシ サーバーで、プロキシ サーバー用のローカル アドレス テーブル (LAT) を定義し、受信待ちするノード アドレスが LAT エントリの範囲外になるようにします。 詳細については、プロキシ サーバーのマニュアルを参照してください。  
  
>  [!NOTE]
>  このトピックの対象は、オンプレミスの [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]です。 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]に関連する接続問題については、 [「Troubleshoot connection issues to Azure SQL Database」](https://docs.microsoft.com/azure/sql-database/sql-database-troubleshoot-common-connection-issues)(Azure SQL Database の接続問題のトラブルシューティング) を参照してください。  


