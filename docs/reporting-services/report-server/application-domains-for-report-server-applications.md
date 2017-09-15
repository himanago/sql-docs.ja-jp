---
title: "レポート サーバー アプリケーションのアプリケーション ドメイン |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application domains [Reporting Services]
- recycling application domains
ms.assetid: a455e2e6-8764-493d-a1bc-abe80829f543
caps.latest.revision: 18
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0cec89b68c69b5e5ae6875d5d5d5e721008844cd
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="application-domains-for-report-server-applications"></a>レポート サーバー アプリケーションのアプリケーション ドメイン
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]では、レポート サーバー Web サービス、レポート マネージャー、およびバックグラウンド処理アプリケーションを含んだ単一のサービスとしてレポート サーバーが実装されます。 それぞれのアプリケーションは、単一のレポート サーバー プロセス内の独自のアプリケーション ドメインで実行されます。 ほとんどの場合、アプリケーション ドメインは内部的に作成、構成、および管理されます。 ただし、レポート サーバーのアプリケーション ドメインがどのようにリサイクルされるのかを理解しておくと、パフォーマンスまたはメモリの問題を調査したり、中断したサービスをトラブルシューティングしたりする際に、その知識を役立てることができます。  
  
> [!NOTE]  
>  基本認証を使用するレポート サーバーでレポート ビルダーへのアクセスを構成すると、レポート ビルダーは独自のアプリケーション ドメインで実行されます。 このアプリケーション ドメインは、サーバー プロセスで実行される他のアプリケーション ドメインとは異なります。 このドメインは、サービス コントローラーで管理され、レポート サーバーのメモリ負荷に応じてメモリの割り当てを再調整するメモリ管理機能の対象ではありません。  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アプリケーションでは、次のようなイベントによってアプリケーション ドメインがリサイクルされます。  
  
-   定期的なリサイクル処理 (決められた間隔で実行)  
  
-   レポート サーバーの構成変更  
  
-   [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] の構成変更  
  
-   メモリ割り当ての失敗  
  
 次の表では、これらのイベントが発生した場合、アプリケーション ドメインがどのようにリサイクルされるかを簡単に説明します。  
  
|イベント|イベントの説明|適用対象|構成可能|リサイクル処理の説明|  
|-----------|-----------------------|----------------|------------------|-----------------------------------|  
|定期的なリサイクル処理 (決められた間隔で実行)|既定では、アプリケーション ドメインは 12 時間おきにリサイクルされます。<br /><br /> 通常、 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] アプリケーションでは、プロセス全体の正常動作を促進するために定期的なリサイクルが行われます。|レポート サーバー Web サービス<br /><br /> レポート マネージャー<br /><br /> バックグラウンド処理アプリケーション|可能。 サイクル間隔は、RSReportServer.config ファイルの**RecycleTime** 構成設定によって異なります。<br /><br /> バックグラウンド処理の完了を待機する最大時間は、**MaxAppDomainUnloadTime** で設定します。|[!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] によって管理されます。<br /><br /> バックグラウンド処理アプリケーションの場合、スケジュールに従って開始された新しいジョブの新しいアプリケーション ドメインがレポート サーバーによって作成されます。 既に進行中のジョブは、最大待ち時間に達しない限り、現在のアプリケーション ドメインで完了することが許可されます。|  
|レポート サーバーの構成変更|RSReportServer.config ファイルを変更した場合、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] によってアプリケーション ドメインがリサイクルされます。|レポート サーバー Web サービス<br /><br /> レポート マネージャー<br /><br /> バックグラウンド処理アプリケーション|不可。|リサイクル処理を抑制することはできません。 ただし、構成の変更に呼応して発生するリサイクル処理については、定期的なリサイクル処理と同じように処理されます。 新しい要求については、新しいアプリケーション ドメインが作成され、現在の要求およびジョブについては、現在のアプリケーション ドメインで実行されます。|  
|[!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]構成の変更|[!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]監視ファイルへの変更がある場合、アプリケーション ドメインがリサイクルされます (machine.config ファイル、Web.config ファイル、たとえば、および[!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]プログラム ファイル)。|レポート サーバー Web サービス<br /><br /> レポート マネージャー|不可。|[!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]操作を管理します。<br /><br /> [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] によって開始されたリサイクル処理は、バックグラウンド処理のアプリケーション ドメインには影響しません。|  
|メモリ不足とメモリ割り当ての失敗|メモリ割り当てに失敗した場合や、サーバーで深刻なメモリ不足が生じている場合、アプリケーション ドメインが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の CLR によって直ちにリサイクルされます。|レポート サーバー Web サービス<br /><br /> レポート マネージャー<br /><br /> バックグラウンド処理アプリケーション|不可。|深刻なメモリ不足が生じた場合、レポート サーバーは、現在のアプリケーション ドメインで、新しい要求を受け付けないようにします。 サーバーが新しい要求を拒否している間は、HTTP 503 エラーが発生します。 古いアプリケーション ドメインがアンロードされるまで、新しいアプリケーション ドメインは作成されません。 したがって、サーバーで深刻なメモリ不足が生じているときに構成ファイルに変更を加えた場合、現在進行中の要求やジョブは開始されることも、完了することもありません。<br /><br /> メモリ割り当てに失敗した場合は、すべてのアプリケーション ドメインが直ちに再起動されます。 進行中の要求およびジョブは破棄されます。 これらのジョブおよび要求は手動で再起動する必要があります。|  
  
## <a name="planned-and-unplanned-recycle-operations"></a>定期的なリサイクル処理と不定期なリサイクル処理  
 リサイクル処理には、定期的な処理と不定期な処理があります。この点は、その処理を引き起こした条件によって異なります。  
  
-   定期的なリサイクル処理は、RSReportServer.config ファイルに定義されている間隔で実行されます。 既定では 12 時間おきに実行されます。 通常、 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] アプリケーションでは、プロセス全体の正常動作を促進するためリサイクルが定期的に行われます。 定期的なリサイクル処理の場合、レポート サーバーは、新しい要求に対応するアプリケーション ドメインを別途作成します。 既に進行中の要求は、最大待ち時間に達しない限り、現在のアプリケーション ドメインで完了することが許可されます。 定期的なリサイクル処理を制御する構成設定は、サーバー全体に対して設定されます。 アプリケーションごとに異なるリサイクル スケジュールまたはメモリしきい値を構成することはできません。  
  
-   不定期的なリサイクル処理は、構成変更、メモリ不足、およびメモリ割り当ての失敗に呼応する形で、任意のタイミングで発生します。  
  
    -   構成の変更が生じた場合、レポート サーバーは、新しい要求をアプリケーション ドメインの新しいインスタンスにリダイレクトする強制力の低いリサイクル処理を試みます。 強制力の低いリサイクル処理に失敗した場合は、強制力の高いリサイクル処理が開始されます。つまり、現在進行中のすべての要求が取り消され、現在のアプリケーション ドメインがシャットダウンされて、アプリケーション ドメインが再起動されます。  
  
    -   メモリ割り当ての失敗は、サーバーが実行しているレポート処理の量に対して、十分なシステム リソースが存在しないことを意味します。 メモリ割り当てに失敗した場合は、すべてのアプリケーション ドメインで、強制力の高いリサイクル処理が実行されます。 要求キューはすべてクリアされます。 取り消された要求は再開されません。 レポートを対話的に閲覧していたユーザーは、レポートを最新の情報に更新するか、開き直す必要があります。 スケジュールされている処理は、次回の予定時刻に実行されます。 この遅延が問題になる場合は、レポート スナップショットを手動で更新するか、サブスクリプションのスケジュールまたはレポートのスナップショット スケジュールを変更し、それらが直ちに実行されるようにしてください。  
  
 レポート サーバー Web サービス、レポート マネージャー、およびバックグラウンド処理アプリケーションでは、リサイクル処理を引き起こした条件に応じて、アプリケーション ドメインのリサイクル処理がそれぞれ別個に実行される場合と、まとめて実行される場合とがあります。  
  
-   [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] によって開始されたリサイクル処理は、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] アプリケーション (つまり、レポート サーバー Web サービスおよびレポート マネージャー) にのみ影響します。 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] は、監視対象のファイルが変更されたかどうかに基づいて、アプリケーション ドメインをリサイクルします。 通常、 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] によって開始されたリサイクル処理は、バックグラウンド処理アプリケーションのリサイクル処理とは無関係に実行されます。  
  
-   通常、レポート サーバーによって開始されたリサイクル処理は、レポート サーバー Web サービス、レポート マネージャー、およびバックグラウンド処理アプリケーションに影響します。 リサイクル処理は、構成設定の変更時やサービスの再起動時に実行されます。  
  
## <a name="rsreportserver-configuration-settings-for-application-domains"></a>アプリケーション ドメインに関係する RSReportServer 構成設定  
 構成設定は、 [RSReportServer.config ファイル](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)で指定されます。 次の例は、アプリケーション ドメインの定期的なリサイクル動作に関係する既定の構成設定を示しています。  
  
 `<RecycleTime>720</RecycleTime>`  
  
 `<MaxAppDomainUnloadTime>30</MaxAppDomainUnloadTime>`  
  
 次の表では、これらの要素について説明します。  
  
|要素|適用対象|定義|  
|-------------|----------------|----------------|  
|**RecycleTime**|3 つの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アプリケーション ドメインすべて|アプリケーション ドメインがリサイクルされる頻度を指定します。 既定のリサイクル スケジュールは、 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] アプリケーションの標準的なドメイン リサイクル パターン (12 時間) に従います。 スケジュールされた時間になると、新規要求はすべてアプリケーション ドメインの新しいインスタンスに転送されます。 元のインスタンスで処理中の要求はそのまま継続して処理されます。 処理がすべて完了すると、元のインスタンスが削除され、新しいインスタンスだけがアクティブなアプリケーション ドメイン インスタンスとなります。<br /><br /> 既定値は 720 分です。|  
|**MaxAppDomainUnloadTime**|バックグラウンド処理アプリケーション ドメインのみ|既定では、リサイクル中にアプリケーション ドメインがシャット ダウンに費やすことのできる時間として、30 分間の待機時間がレポート サーバーによって割り当てられます。 処理中のジョブが割り当てられた時間内に完了しない場合 (処理に必要な時間が待機時間よりも長くなる場合)、アプリケーション ドメインのインスタンスが直ちに再起動されます。 未完了のジョブはすべて終了されます。<br /><br /> レポート サーバーで実行されているジョブのステータスを表示したり取り消したりする方法の詳細については、「[Cancel Report Server Jobs &#40;Management Studio&#41;](../../reporting-services/tools/cancel-report-server-jobs-management-studio.md)」([レポート サーバー ジョブのキャンセル] &#40;Management Studio&#41;) を参照してください。|  
  
> [!NOTE]  
>  IIS でホストされた [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] アプリケーションの machine.config には、リサイクルのスケジュールが指定されている場合もあります。レポート サーバー Web サービスもレポート マネージャーも [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] アプリケーションですが、この構成ファイルで指定されているアプリケーション ドメインのリサイクル スケジュールは、どちらのアプリケーションにも適用されません。  
  
## <a name="see-also"></a>参照  
 [RsReportServer.config 構成ファイル](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
 [Reporting Services の構成ファイル &#40; を変更します。RSreportserver.config &#41;](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)   
 [レポート サーバー アプリケーションの使用可能なメモリを構成します。](../../reporting-services/report-server/configure-available-memory-for-report-server-applications.md)  
  
  