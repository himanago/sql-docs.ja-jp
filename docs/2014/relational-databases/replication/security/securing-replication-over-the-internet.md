---
title: インターネット経由のレプリケーションのセキュリティ | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- security [SQL Server replication], Internet
- Internet [SQL Server replication], security
ms.assetid: 25b7af05-2721-4b24-9083-fb671e8bf4e0
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 55320406ef9fd56feafa9fcf65883e2b68eae329
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48152165"
---
# <a name="securing-replication-over-the-internet"></a>インターネット経由のレプリケーションのセキュリティ
  インターネット経由のレプリケーションを利用すると、特にモバイルのサブスクライバーで必要とされるような柔軟性を実現できます。ただし、適切に構成して十分なセキュリティを確保する必要があります。 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] では、インターネット経由で情報を安全に共有するために、次のいずれかの技術を使用することを推奨しています。  
  
-   仮想プライベート ネットワーク (VPN)  
  
-   マージ レプリケーション用の Web 同期オプション  
  
## <a name="virtual-private-network"></a>仮想プライベート ネットワーク  
 仮想プライベート ネットワークを使用すると、複数の層を使ったシンプルかつ安全な方法で、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のデータをインターネット経由でレプリケートできます。 インターネットを介しての VPN 接続は、論理的にはサイト間のワイド エリア ネットワーク (WAN) リンクとして動作します。  
  
 これは、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows&#xA0;NT Version&#xA0;4.0 または [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows&#xA0;2000 オペレーティング システムで使用できる [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Point-to-Point トンネリング プロトコル (PPTP)、または Windows&#xA0;2000 オペレーティング システムで使用できるレイヤー 2 トンネリング プロトコル (L2TP) などのプロトコルを使用して、ユーザーがインターネットや他のパブリック ネットワークをトンネリングできるようにすることで実現します。 これにより、プライベート ネットワークとほぼ同等のセキュリティと機能が実現されます。  
  
 VPN の設定の詳細については、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows のマニュアルを参照してください。  
  
## <a name="web-synchronization-through-iis"></a>IIS による Web 同期  
 マージ レプリケーション用の Web 同期オプションを使用すると、HTTPS プロトコルを使用してデータをレプリケートできます。この方法は、ファイアウォール越しにデータをレプリケートする場合に便利です。 詳細については、「[Web 同期の構成](../configure-web-synchronization.md)」および「[Web 同期のセキュリティ アーキテクチャ](security-architecture-for-web-synchronization.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Replication Security Best Practices](replication-security-best-practices.md)   
 [セキュリティと保護 &#40;レプリケーション&#41;](security-and-protection-replication.md)  
  
  
