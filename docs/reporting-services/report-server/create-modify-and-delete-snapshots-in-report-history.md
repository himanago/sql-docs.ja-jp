---
title: "作成、変更、およびレポート履歴のスナップショットを削除 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- snapshots [Reporting Services]
- report snapshots [Reporting Services]
ms.assetid: 5aebbbfa-a8db-462d-8ab9-746fad9525f0
caps.latest.revision: 40
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 4c3d0de81994b5a234ead420277718c760f9ddb3
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="create-modify-and-delete-snapshots-in-report-history"></a>レポート履歴のスナップショットの作成、変更および削除
  レポート履歴は、一連のレポート スナップショットです。 スナップショットの追加と削除、またはレポート履歴の記憶域に影響するプロパティの変更を行うことで、レポート履歴を管理できます。 レポート履歴は手動で、またはスケジュールに従って作成できます。  
  
 レポート履歴を作成するには、ロールの割り当てに "レポート履歴の管理" タスクが含まれている必要があります。 レポート履歴を表示するには、ロールの割り当てに "レポートの表示" タスクが含まれている必要があります。 レポート履歴は、レポートにアクセスできるすべてのユーザーが利用できます。 一部のユーザーを対象に、レポート履歴の有効化または無効化を選択的に行うことはできません。  
  
 レポート履歴のスナップショットは、スナップショットの作成日時で識別されます。 その日時は、クエリが実行された日時に基づいています。  
  
## <a name="creating-snapshots-in-report-history"></a>レポート履歴でのスナップショットの作成  
 スナップショットは、自動的に実行できる任意のレポートに、手動で、またはスケジュールされた間隔で、作成できます。 レポートを自動的に実行するには、保存されている資格情報を使用するか、資格情報を使用しないようにする必要があります。 また、レポートでパラメーターを使用する場合、レポートの実行時に使用する既定値を指定する必要があります。 レポートのプロパティ ページで、格納された資格情報とパラメーター値を指定できます。 詳細については、「[[パラメーター] プロパティ ページ (レポート マネージャー)](http://msdn.microsoft.com/library/ebb53598-2378-46ae-8935-d5192f8ea49a)」を参照してください。  
  
 レポート スナップショットを作成すると、レポート スナップショットと共に、以下の要素がレポート サーバー データベースに格納されます。  
  
-   結果セット (レポートの [データ ソース] プロパティ ページで指定した資格情報によって取得される、レポート内のデータ)。  
  
-   基になるレポート定義。これは、スナップショットを作成した時点で存在するものです。 スナップショットを生成した後にレポート定義を変更する場合、これらの変更はスナップショットに反映されません。  
  
-   結果セットの取得またはフィルター処理に使用するパラメーター値。  
  
-   画像などの埋め込みリソース。 レポートにリンクされている外部リソースは、レポート スナップショットと共には格納されません。  
  
 レポート履歴を作成する方法、および格納できるレポート スナップショット数は、設定によって決まります。  
  
 レポートでエラーが発生した場合、スナップショットは作成されません。 警告が発生してもそのまま動作するレポートは、スナップショットの生成に使用できます。  
  
## <a name="modifying-properties-and-deleting-report-history"></a>プロパティの変更およびレポート履歴の削除  
 レポート スナップショットを作成した後に変更することはできません。 ただし、プロパティを変更することはできます。この場合、レポート履歴は削除されます。  
  
 レポート履歴は、以下の方法で削除できます。  
  
-   1 つずつ、またはまとめて、スナップショットを手動で削除します。  
  
     レポート マネージャーで、[履歴] ページからスナップショットを削除できます。 レポートに移動して [履歴] をクリックし、削除するスナップショットの隣にあるチェック ボックスをオンにして、 **[削除]**をクリックします。  
  
-   レポート履歴の制限を低くして、格納されているスナップショット数を減らします。 レポート履歴の制限は、レポート サーバーに対して、または特定のレポートに対して設定できます。 制限値を下げた場合、最も古いスナップショットが履歴から削除されます。  
  
 レポート サーバーに格納されているすべてのレポート履歴を、一括操作で削除することはできません。  
  
 また、レポートを削除するとレポート履歴も削除されます。 たとえば、月間の売上レポートを新しい売上レポートに置き換えるために削除する場合、そのレポートに関連付けられたすべてのレポート履歴も削除されます。 ただし、レポートを移動する場合、すべてのレポート履歴がそのレポートと共に移動されます。  
  
## <a name="see-also"></a>参照  
 [レポート履歴 &#40; を作成します。Reporting Services の SharePoint モード &#41; と統合](../../reporting-services/report-server/create-report-history-reporting-services-in-sharepoint-integrated-mode.md)   
 [レポート マネージャーと &#40; です。SSRS ネイティブ モードと &#41; です。](http://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896)   
 [レポート サーバー コンテンツの管理 &#40;SSRS ネイティブ モード&#41;](../../reporting-services/report-server/report-server-content-management-ssrs-native-mode.md)   
 [レポート履歴と &#40; にスナップショットを追加します。レポート マネージャーと &#41; です。](../../reporting-services/report-server/add-a-snapshot-to-report-history-report-manager.md)   
 [レポート履歴を制限 & #40 です。レポート マネージャー &#41;](../../reporting-services/reports/limit-report-history-report-manager.md)  
  
  