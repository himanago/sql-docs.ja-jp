---
title: タスクとアクセス許可 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- permissions [Reporting Services], tasks
- role-based security [Reporting Services], permissions
- security [Reporting Services], tasks
- security [Reporting Services], permissions
- role-based security [Reporting Services], tasks
- predefined tasks [Reporting Services]
- tasks [Reporting Services]
ms.assetid: d7ff90b5-b976-4270-b9ad-9d7b801d8263
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: ce940bd22b9fbc5d2628cdeae3a0eea376f2bc99
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48165282"
---
# <a name="tasks-and-permissions"></a>タスクと権限
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]における *タスク* とは、ユーザーまたは管理者が実行できるアクションのことです。 タスクは事前に定義されています。 カスタム タスクを作成したり、プログラムまたはツールから提供されるタスクを変更することはできません。 タスクは全部で 25 種類あります。 これらのタスクにより、ロールベースのセキュリティで実行できる操作の全体が構成されています。 タスクの例としては、"レポートの表示"、"レポートの管理"、"レポート サーバーのプロパティを管理" などがあります。  
  
 各タスクは、同様に事前定義されている一連の権限で構成されます。 たとえば、"フォルダーの管理" タスクには、フォルダーを作成および削除する権限や、フォルダーのプロパティを表示および更新する権限が含まれています。 各タスクに対する権限は、各タスクをより詳細に説明するために記述されています。 権限を直接操作したり、ロールの割り当てで指定したりすることはできません。 ユーザーは、ロールの定義に含まれているタスクから間接的に権限を与えられます。  
  
 タスクは、そのタスクがロールの一部であり、そのロールがロールの割り当てに含まれている場合にのみ実行できます。 そのため、たとえば "モデルの表示" タスクがロールに含まれていない場合や、そのロールがロールの割り当てに含まれていない場合、ユーザーはレポート モデルを表示できません。 次の図では、権限がタスクにどのように組み込まれるか、および特定のロールの割り当てに使用できるロールにタスクがどのように組み込まれるかを示します。  
  
 ![アクセス許可とタスク図](../media/report-securityobjects.gif "アクセス許可とタスク図")  
権限とタスク図  
  
## <a name="system-and-item-level-tasks"></a>システムレベルおよびアイテムレベルのタスク  
 タスクは、システムレベルとアイテムレベルの 2 つのカテゴリに分類されます。 ロールは、単一のカテゴリからのみタスクを含めることができます。 次の表で、タスクの各カテゴリについて説明します。  
  
|カテゴリ|説明|  
|--------------|-----------------|  
|[アイテムレベルのタスク](tasks-and-permissions-item-level-tasks.md)|フォルダー、レポート、レポート モデル、リソースなど、レポート サーバーで管理されるアイテムに対して実行されるアクションです。<br /><br /> アイテムレベルのタスクは、レポート サーバー フォルダーの名前空間に対して有効です。 レポート サーバーのフォルダーまたは URL によってアクセスするすべてのアイテムは、アイテムレベルのタスクを含んだロールの割り当てによってセキュリティ保護されています。|  
|[システムレベルのタスク](tasks-and-permissions-system-level-tasks.md)|ジョブまたは共有スケジュールの管理などの、システムレベルで実行されるアクションです。これらのアクションは、多くのアイテムで使用できます。 システムレベルのタスクは、レポート サーバー フォルダーの名前空間の外部に対して有効です。|  
  
## <a name="see-also"></a>参照  
 [ロールの定義](role-definitions.md)   
 [定義済みロール](role-definitions-predefined-roles.md)   
 [ネイティブ モードのレポート サーバーに対する権限の許可](granting-permissions-on-a-native-mode-report-server.md)  
  
  
