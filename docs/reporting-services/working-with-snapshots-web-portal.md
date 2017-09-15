---
title: "スナップショット (web ポータル) の操作 |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/02/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9ae20556-e243-4a60-b076-9fd9e82c7355
caps.latest.revision: 6
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: dcf26be9dc2e502b2d01f5d05bcb005fd7938017
ms.openlocfilehash: 2bca4e3089bde763669c4fe518f509fbe94cb6eb
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---

# <a name="working-with-snapshots-web-portal"></a>スナップショットの操作 (Web ポータル)

[!INCLUDE[ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../includes/ssrs-appliesto-pbirs.md)]

スナップショットを選択して、レポートの作成を指定できます、**省略記号 (...)** 、レポートの選択**管理**を選択して**キャッシュ**または**履歴スナップショット**です。  
  
> [!NOTE]
> SQL Server エージェント サービスを開始する必要があります。  
   
キャッシュ スナップショットを作成して、特定の実行プロパティの読み込み速度を高めることができます。 また、履歴スナップショットで特定の時点をキャプチャすることもできます。  
  
## <a name="creating-a-cache-snapshot"></a>キャッシュ スナップショットを作成する  
  
スナップショットを作成するには、次のようにします。  
  
![ssRSWebPortal-report-caching4](../reporting-services/media/ssrswebportal-report-caching4.png)  
  
1.  **[キャッシュ]** ページで、 **[常に事前生成されたスナップショットに対してこのレポートを実行する]** を選択して、スナップショットを作成するためのオプションを有効にします。  
  
2.  スケジュールに従って定期的にスナップショットを作成する場合は、 **[スケジュールに従ってキャッシュ スナップショットを作成する]** を選択します。 これで、共有スケジュールを使用、またはカスタム スケジュールを定義してスナップショットを更新できます。  
  
3.  今すぐキャッシュ スナップショットを作成するには、 **[このページの [適用] をクリックした時点でキャッシュ スナップショットを作成する]** を選択します。 このオプションのみを選択すると、スナップショットは更新されません。  
  
## <a name="create-modify-and-delete-history-snapshots"></a>履歴スナップショットの作成、変更および削除  
  
履歴スナップショットを使用するには、レポートの管理で **[履歴スナップショット]**を選択します。  
  
**[履歴スナップショット]** ページには、一定期間に生成および保存したレポート スナップショットが表示されます。 レポート サーバーで設定されているオプションによっては、新しいスナップショットのみが履歴に保存されます。  
  
レポート ヒストリは、常に元のレポートのコンテキスト内で表示されます。 すべてのレポートのヒストリをレポート サーバーの 1 か所に表示することはできません。  
  
履歴スナップショットを生成するには、レポートが自動的に実行されるようにする必要があります (つまり、保存されている資格情報を使用する必要があります。また、パラメーター化されたレポートには、すべてのパラメーターの既定のパラメーター値を含める必要があります)。 レポート ヒストリの生成は、手動またはスケジュールに設定した操作によって行うことができます。 レポート ヒストリの作成方法は、レポートのヒストリ プロパティによって決まります。  
  
![ssRSWebPortal-historysnapshots1](../reporting-services/media/ssrswebportal-historysnapshots1.png)  
   
1.  履歴スナップショットを作成するには、 **[新しい履歴スナップショット]**を選択します。 レポートが処理され、一覧にエントリが追加されます。  
  
2.  スケジュールと保持ポリシーを定義するには、設定に移動します。  
  
3.  履歴スナップショットをクリックすると、そのスナップショットが表示されます。 レポート ヒストリに表示されるスナップショットは、作成日時だけで識別されます。 スナップショットがスケジュールの設定を受けて生成されたのか、手動で生成されたのかを識別する表示はありません。  
  
### <a name="schedule-and-settings"></a>スケジュールと設定  
  
**[スケジュールと設定]** には、スケジュールを設定し作成したスナップショットの保有期間を制御するオプションが用意されています。  
  
![ssRSWebPortal-historysnapshots2](../reporting-services/media/ssrswebportal-historysnapshots2.png)  
   
必要に応じて、スナップショットを作成するスケジュールを設定できます。 他のユーザーによる新しいスナップショットの作成を防ぐこともできます。 **[ユーザーが手動でスナップショットを作成することを許可する]** をオフにすると、 **新しい履歴スナップショットの作成ボタン**が無効になります。  
  
スナップショットの保有方法を定義することもできます。  
  
**[レポート履歴に含まれるキャッシュ スナップショットも保存する]**  
  
これをオンにすると、レポート実行プロパティを基に生成したレポート スナップショットがレポート履歴にコピーされます。 生成したスナップショットからレポートを実行するようにレポート実行プロパティを設定できます。 このレポート ヒストリのプロパティを設定すると、一定期間に生成されたすべてのレポート スナップショットのコピーをレポート ヒストリに配置することで、その記録を保存できます。

## <a name="next-steps"></a>次の手順

[Web ポータル](../reporting-services/web-portal-ssrs-native-mode.md)  
[改ページ調整されたレポートの使用](working-with-paginated-reports-web-portal.md)  
[共有データセットを操作します。](../reporting-services/work-with-shared-datasets-web-portal.md)

他に質問しますか。 [Reporting Services のフォーラムで質問してみてください。](http://go.microsoft.com/fwlink/?LinkId=620231)