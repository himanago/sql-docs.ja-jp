---
title: カタログ アイテムの削除 (Management Studio) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: tools
ms.topic: conceptual
f1_keywords:
- sql13.swb.reportserver.deleteitems.f1
ms.assetid: b0599e01-6dc3-4484-80d4-022a412e0ebd
author: markingmyname
ms.author: maghan
ms.openlocfilehash: fc1cdce9ed2e26874eaa19cff7ad9634880fd1db
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47792120"
---
# <a name="delete-catalog-items-management-studio"></a>カタログ アイテムの削除 (Management Studio)
  このページを使用すると、共有スケジュールとロール定義を削除できます。  
  
 複数のレポートおよびサブスクリプションによって使用される共有スケジュールを削除した場合、以前にその共有スケジュールを使用していたレポートおよびサブスクリプションごとに別個のスケジュールが作成されます。 新たに作成される各スケジュールには、共有スケジュールで指定されていた日付、時刻、および定期的なパターンが保持されます。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] には、個々のスケジュールを一元管理する手段は存在しません。 共有スケジュールを削除した場合、それ以降は、各アイテムのスケジュール情報を個別に管理する必要があります。 共有スケジュールを削除する前に、 [[レポート] ページ](../../reporting-services/tools/schedule-properties-reports-page.md) を使用して、どのレポートが共有スケジュールを現在使用しているかを確認します。  
  
 ロール定義のうち削除できるのは、ロールの割り当てに現在使用されていないものだけです。 現在使用されているロールを削除しようとすると、レポート サーバーでロールが削除されずにエラー メッセージが表示されます。 このページに含まれるロール定義が 1 つだけで、それが現在使用されていない場合、 **[OK]** をクリックするとその定義が削除されます。 このページに複数のロールが含まれている場合、保持するロールと削除するロールを選択することはできません。 **[OK]** をクリックすると、使用されていないロール定義がすべて削除されます。  
  
 削除操作は元に戻せません。 削除したアイテムを復旧するには、そのアイテムを再作成するか、レポート サーバー データベースのバックアップ コピーを復元する必要があります。  
  
## <a name="options"></a>[変数]  
 **名前**  
 削除するアイテムの名前を指定します。  
  
 **型**  
 削除するアイテムの種類を表示します。  
  
 **所有者**  
 所有者の名前を表示します。 ほとんどの場合は [システム] です。  
  
 **ステータス**  
 削除操作の進行状況を表示します。  
  
 **Error**  
 アイテムの削除中にエラーが発生した場合はエラー コードを表示します。  
  
## <a name="see-also"></a>参照  
 [アイテムの削除 &#40;Management Studio&#41;](../../reporting-services/tools/delete-an-item-management-studio.md)   
 [Management Studio のレポート サーバーの F1 ヘルプ](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
 [スケジュールの作成、変更、および削除](../../reporting-services/subscriptions/create-modify-and-delete-schedules.md)  
  
  
