---
title: "バージョン (マスター データ サービス) |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- version flags [Master Data Services], about version flags
- versions [Master Data Services]
- version flags [Master Data Services]
- versions [Master Data Services], version flags
ms.assetid: 752ec96d-53d7-4160-8ed2-92e0324645f3
caps.latest.revision: 9
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 4aa3e9252b57b596ab576616820bbad706a4ea92
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="versions-master-data-services"></a>バージョン (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] では、モデル内に複数のバージョンのマスター データを作成できます。 データを検証している間はバージョンをロックし、データが検証した後にコミットすることができます。 コミットされたバージョンは、変更の監査可能なレコードを形成します。 作成される各バージョンには、モデルのすべてのメンバー、属性値、階層メンバー、階層リレーションシップ、およびコレクションが含まれます。  
  
## <a name="when-to-use-versions"></a>バージョンを使用するタイミング  
 バージョンは、次の場合に使用します。  
  
-   時間と共に変化するマスター データの監査可能なレコードを保持する場合。  
  
-   ビジネス ルールに対してすべてのデータが正常に検証されるようにする間、ユーザーによる変更を防止する場合。  
  
-   サブスクライブ システムによって使用されるようにモデルをロック ダウンする場合。  
  
-   さまざまな階層をすぐに実装しないでテストする場合。  
  
> [!NOTE]  
>  新しいエンティティまたはドメイン ベースの属性を作成するなど、モデルの構造を変更すると、その変更がすべてのバージョンに適用されます。 以前のバージョンのモデルを表示すると、エンティティまたは属性は表示されますが、データは存在しません。  
  
## <a name="version-flags"></a>バージョン フラグ  
 バージョンがユーザーまたはサブスクライブ システムによって使用される状態になったら、バージョンを識別するためのフラグを設定できます。 このフラグは、必要に応じてバージョン間で移動できます。 フラグによって、ユーザーおよびサブスクライブ システムは使用するモデルのバージョンを識別できます。  
  
## <a name="workflow-for-version-management"></a>バージョン管理のワークフロー  
 次のワークフローを使用して、バージョン管理を行います。  
  
1.  最初のバージョンは、モデルを作成して [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースに会社のマスター データを入力すると、自動的に作成されます。 ユーザーは権限に基づいて、必要に応じてこのバージョンを変更できます。  
  
2.  モデルのバージョンをコミットする場合は、モデル管理者のみがデータを更新できるように、バージョンをロックします。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](../master-data-services/administrators-master-data-services.md)」を参照してください。 通知が構成されている場合、バージョンのステータスが変更されるたびに電子メール通知がモデル管理者に送信されます。 詳細については、「[電子メール通知を構成する (マスター データ サービス)](../master-data-services/configure-email-notifications-master-data-services.md)」を参照してください。  
  
3.  ロックしたバージョンのデータにビジネス ルールを適用し、検証の問題がないか確認します。 必要に応じて、不足している情報を入力したり、問題の原因となったトランザクションを破棄したりできます。 ユーザーが変更できるように、バージョンのロックを解除することもできます。  
  
4.  すべてのデータが検証に合格したら、バージョンをコミットし、サブスクライブ システムで使用できるようにバージョンにフラグを設定します。 コミットしたバージョンを変更することはできません。  
  
5.  コミットしたバージョンをコピーし、ユーザーに新しいバージョンのモデルで作業できるようになったことを通知します。  
  
## <a name="sequential-or-simultaneous-versions"></a>順次バージョンまたは同時バージョン  
 モデルの順次バージョンまたは同時バージョンを作成できます。  
  
-   **順次バージョン。** バージョンをコミットするたびに、新しいコピーを作成して、バージョンに次の連続番号を付けます。 たとえば、 **バージョン 7** のモデルをコピーし、そのコピーに **バージョン 8**という名前を付けることができます。  
  
-   **同時バージョン。** 一度に 2 つ以上のバージョンのデータで作業を行う場合は、モデルの同時バージョンを作成します。 同時バージョンは、通常の業務と並行して会社の再編や合併を行う場合に、新しいマスター データを既存の構造に適合させる方法を決める際に役立ちます。  
  
    > [!NOTE]  
    >  [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] の設定によって、すべてのバージョンをコピーできるか、またはコミットされたバージョンのみをコピーできるかが決まります。 同時バージョンを作成するには、すべてのバージョンをコピーできるように [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] を構成する必要があります。 この設定は、System Settings テーブルでも行うことができます。 詳細については、「[システム設定 &#40;マスター データ サービス&#41;](../master-data-services/system-settings-master-data-services.md)」を参照してください。  
  
## <a name="related-tasks"></a>関連タスク  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|既存のバージョンの名前を変更する。|[バージョン名 &#40; を変更します。マスター データ サービス &#41;](../master-data-services/change-a-version-name-master-data-services.md)|  
|管理者のみがデータを編集できるようにバージョンをロックする。|[ロックのバージョンと #40 です。マスター データ サービス &#41;](../master-data-services/lock-a-version-master-data-services.md)|  
|ユーザーがデータを編集できるようにバージョンのロックを解除する。|[バージョン &#40; をロック解除します。マスター データ サービス &#41;](../master-data-services/unlock-a-version-master-data-services.md)|  
|すべてのデータを検証した後にバージョンをコミットする。|[コミット済み & #40 です。マスター データ サービス &#41;](../master-data-services/commit-a-version-master-data-services.md)|  
|新しいフラグを作成してバージョンをマークする。|[バージョン フラグ &#40; を作成します。マスター データ サービス &#41;](../master-data-services/create-a-version-flag-master-data-services.md)|  
|既存のバージョンのフラグ名を変更する。|[バージョン フラグ名 &#40; を変更します。マスター データ サービス &#41;](../master-data-services/change-a-version-flag-name-master-data-services.md)|  
|既存のフラグをバージョンに割り当てる。|[バージョン &#40; にフラグを割り当てるマスター データ サービス &#41;](../master-data-services/assign-a-flag-to-a-version-master-data-services.md)|  
|既存のバージョンの新しいコピーを作成する。|[バージョン &#40; をコピーします。マスター データ サービス &#41;](../master-data-services/copy-a-version-master-data-services.md)|  
|既存のバージョンを削除する。|[バージョンを削除する (マスター データ サービス)](../master-data-services/delete-a-version-master-data-services.md)|  
|論理削除したメンバーをバージョンから削除する|[バージョン メンバーのパージ (マスター データ サービス)](../master-data-services/purge-version-members-master-data-services.md)|  
  
## <a name="related-content"></a>関連コンテンツ  
  
-   [取り消すトランザクション & #40 です。マスター データ サービス &#41;](../master-data-services/reverse-a-transaction-master-data-services.md)  
  
-   [通知 & #40 です。マスター データ サービス &#41;](../master-data-services/notifications-master-data-services.md)  
  
-   [ビジネス ルール & #40 です。マスター データ サービス &#41;](../master-data-services/business-rules-master-data-services.md)  
  
  