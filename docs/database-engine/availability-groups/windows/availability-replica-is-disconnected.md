---
title: "可用性レプリカが切断されている | Microsoft Docs"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.agdashboard.arp2connected.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 1a2162d3-54fb-4356-b349-effbdc15a5a4
caps.latest.revision: 12
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: cfea4350f0958b61db6f71c9cb320a1e51e8f2ad
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="availability-replica-is-disconnected"></a>可用性レプリカが切断されている
    
## <a name="introduction"></a>概要  
  
|||  
|-|-|  
|**ポリシー名**|可用性レプリカの接続状態|  
|**問題点**|可用性レプリカの接続が解除されます。|  
|**カテゴリ**|**重大**|  
|**ファセット**|可用性レプリカ|  
  
## <a name="description"></a>説明  
 このポリシーは、可用性レプリカ間の接続状態を確認します。 可用性レプリカ間の接続状態が DISCONNECTED の場合、ポリシーは通常とは異なる状態です。 それ以外の場合、ポリシーは正常な状態です。  
  
> [!NOTE]  
>  [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]のこのリリース向けに、TechNet Wiki の「 [可用性レプリカの接続が解除される](http://go.microsoft.com/fwlink/p/?LinkId=220857) 」に、考えられるエラーの原因および解決方法に関する情報が紹介されています。  
  
## <a name="possible-causes"></a>考えられる原因  
 セカンダリ レプリカがプライマリ レプリカに接続されていません。 接続状態は DISCONNECTED です。 この問題は、次の状況で発生する可能性があります。  
  
-   接続ポートが他のアプリケーションと競合状態にある。  
  
-   暗号化の種類またはアルゴリズムが一致しない。  
  
-   接続エンドポイントが削除されているか、開始されていない。  
  
-   トランスポートが切断されている。  
  
## <a name="possible-solutions"></a>考えられる解決策  
 この問題に対して考えられる解決策を次に示します。  
  
-   プライマリ レプリカおよびセカンダリ レプリカのインスタンスのデータベース ミラーリング エンドポイントの構成を確認し、対応していない構成を更新します。  
  
-   ポートが競合しているかどうかを確認し、競合している場合はポート番号を変更します。  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループの概要 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
