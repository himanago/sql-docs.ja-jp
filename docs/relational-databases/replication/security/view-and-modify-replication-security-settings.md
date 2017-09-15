---
title: "レプリケーションのセキュリティ設定の表示および変更 | Microsoft Docs"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- modifying replication security settings
- replication [SQL Server], security
- security [SQL Server replication], viewing settings
- viewing replication security settings
- security [SQL Server replication], modifying settings
ms.assetid: 67d79532-1482-4de1-ac9f-4a23d162c85e
caps.latest.revision: 47
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e4e8eb9804660085223e0845adeb093511871316
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="view-and-modify-replication-security-settings"></a>レプリケーションのセキュリティ設定の表示および変更
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、レプリケーションのセキュリティ設定を表示および変更する方法について説明します。 たとえば、ログ リーダー エージェントからパブリッシャーへの接続を SQL Server 認証から Windows 統合認証に変更したい場合や、Windows アカウントのパスワードを変更したときにエージェント ジョブの実行に使用する資格情報を変更したい場合があります。 各エージェントで必要な権限の詳細については、「[Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md)」(レプリケーション エージェントのセキュリティ モデル) をご覧ください。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [セキュリティ](#Security)  
  
-   **レプリケーションのセキュリティ設定を表示および変更するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [レプリケーション管理オブジェクト (RMO)](#RMOProcedure)  
  
-   **フォロー アップ:**  [レプリケーションのセキュリティ設定を変更した後](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   使用するストアド プロシージャは、エージェントの種類およびサーバー接続の種類によって異なります。  
  
-   使用する RMO のクラスとプロパティは、エージェントの種類およびサーバー接続の種類によって異なります。  
  
###  <a name="Security"></a> セキュリティ  
 セキュリティ上の理由から、レプリケーション ストアド プロシージャによって返される結果セットでは、パスワードの実際の値はマスクされます。  
  
####  <a name="Permissions"></a> アクセス許可  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 次のダイアログ ボックスでセキュリティ設定を表示および変更します。  
  
1.  **[レプリケーション パスワードの更新]** ダイアログ ボックス。このダイアログ ボックスは、 **の** [レプリケーション] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]フォルダーから利用できます。 レプリケーション トポロジのサーバーで [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] アカウントまたは Windows アカウントのパスワードを変更する場合は、そのアカウントを使用する各エージェントのパスワードを更新するよりも、このダイアログ ボックスを使用してください。 複数のサーバー上のエージェントが同じアカウントを使用している場合は、それぞれのサーバーに接続してパスワードを変更する必要があります。 パスワードは、レプリケーションで使用されるすべての場所で更新されます。 パスワードは、リンク サーバーなど、その他の場所では更新されません。  
  
2.  **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[エージェント セキュリティ]** ページ。 このダイアログ ボックスへのアクセスの詳細については、「 [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)」を参照してください。  
  
3.  **[サブスクリプションのプロパティ - \<Subscription>]** ダイアログ ボックス。 このダイアログ ボックスへのアクセスの詳細については、「 [プッシュ サブスクリプションのプロパティの表示または変更](../../../relational-databases/replication/view-and-modify-push-subscription-properties.md) 」および「 [プル サブスクリプションのプロパティの表示または変更](../../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)」を参照してください。  
  
4.  **[ディストリビューターのプロパティ - \<Distributor>]** ダイアログ ボックスと **[ディストリビューション データベースのプロパティ - \<Database>]** ダイアログ ボックス。 これらのダイアログ ボックスへのアクセスの詳細については、「 [ディストリビューターとパブリッシャーのプロパティの表示および変更](../../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)」を参照してください。  
  
5.  **[パブリッシャーのプロパティ - \<Publisher>]** ダイアログ ボックス。 このダイアログ ボックスへのアクセスの詳細については、「 [ディストリビューターとパブリッシャーのプロパティの表示および変更](../../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)」を参照してください。  
  
#### <a name="to-change-the-password-for-an-account-used-by-one-or-more-agents"></a>1 つ以上のエージェントによって使用されるアカウントのパスワードを変更するには  
  
1.  アカウントが SQL Server アカウントの場合、このダイアログ ボックスによって SQL Server アカウントのパスワードも変更されます。 アカウントが Windows アカウントの場合は、最初に Windows でパスワードを変更します。 詳細については、Windows のマニュアルを参照してください。  
  
    > [!NOTE]  
    >  レプリケーション パスワードを変更したら、そのパスワードを使用する各エージェントを停止して再起動し、エージェントに対して変更を反映させる必要があります。  
  
2.  [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]でサーバーに接続して、サーバー ノードを展開します。  
  
3.  **[レプリケーション]** フォルダーを右クリックし、 **[レプリケーション パスワードの更新]**をクリックします。  
  
4.  **[レプリケーション パスワードの更新]** ダイアログ ボックスで、アカウントと新しいパスワードを指定します。  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-change-security-settings-for-the-snapshot-agent"></a>スナップショット エージェントのセキュリティ設定を変更するには  
  
1.  **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[エージェント セキュリティ]** ページで、**[スナップショット エージェント]** テキスト ボックスの横にある **[セキュリティ設定]** ボタンをクリックします。  
  
2.  **[スナップショット エージェントのセキュリティ]** ダイアログ ボックスで、エージェントを実行するアカウントを指定します。  
  
    -   **[プロセス アカウント]** テキスト ボックスに新しい Windows アカウントを入力します。  
  
    -   **[パスワード]** テキスト ボックスと **[パスワードの確認入力]** テキスト ボックスに、新しい複雑なパスワードを入力します。  
  
3.  エージェントがディストリビューターからパブリッシャーに接続するときのコンテキストを指定します。 **[次の SQL Server ログインを使用する]**を選択する場合は、ログインも指定する必要があります。  
  
    -   **[ログイン]** テキスト ボックスにログインを入力します。  
  
    -   **[パスワード]** テキスト ボックスと **[パスワードの確認入力]** テキスト ボックスに、新しい複雑なパスワードを入力します。  
  
    > [!NOTE]  
    >  パブリッシャーが Oracle パブリッシャーの場合は、接続のコンテキストを **[ディストリビューターのプロパティ - \<Distributor>]** ダイアログ ボックスで指定します。 コンテキストを変更する手順については、以下を参照してください。  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-change-security-settings-for-the-log-reader-agent"></a>ログ リーダー エージェントのセキュリティ設定を変更するには  
  
1.  **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[エージェント セキュリティ]** ページで、**[ログ リーダー エージェント]** テキスト ボックスの横にある **[セキュリティ設定]** ボタンをクリックします。  
  
2.  **[ログ リーダー エージェントのセキュリティ]** ダイアログ ボックスで、エージェントを実行するアカウントを指定します。  
  
    -   **[プロセス アカウント]** テキスト ボックスに新しい Windows アカウントを入力します。  
  
    -   **[パスワード]** テキスト ボックスと **[パスワードの確認入力]** テキスト ボックスに、新しい複雑なパスワードを入力します。  
  
3.  エージェントがディストリビューターからパブリッシャーに接続するときのコンテキストを指定します。 **[次の SQL Server ログインを使用する]**を選択する場合は、ログインも指定する必要があります。  
  
    -   **[ログイン]** テキスト ボックスにログインを入力します。  
  
    -   **[パスワード]** テキスト ボックスと **[パスワードの確認入力]** テキスト ボックスに、新しい複雑なパスワードを入力します。  
  
    > [!NOTE]  
    >  パブリッシャーが Oracle パブリッシャーの場合は、接続のコンテキストを **[ディストリビューターのプロパティ - \<Distributor>]** ダイアログ ボックスで指定します。 次の手順を使用して、コンテキストを変更します。  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  ログ リーダー エージェントは、パブリッシュされているデータベースごとに 1 つ存在します。 1 つのパブリケーションでエージェントのセキュリティ設定を変更すると、パブリケーション データベースのすべてのパブリケーションの設定に影響が及びます。  
  
#### <a name="to-change-the-context-under-which-the-snapshot-agent-and-log-reader-agent-for-an-oracle-publication-make-connections-to-the-publisher"></a>Oracle パブリケーションのスナップショット エージェントおよびログ リーダー エージェントがパブリッシャーに接続するときのコンテキストを変更するには  
  
1.  **[ディストリビューターのプロパティ - \<Distributor>]** ダイアログ ボックスの **[パブリッシャー]** ページで、パブリッシャーの横にあるプロパティ ボタン (**...**) をクリックします。  
  
2.  **[パブリッシャーへのエージェント接続]** セクションで、構成したレプリケーション管理ユーザー スキーマによって使用されるログインとパスワードを指定します。 詳細については、「[Configure an Oracle Publisher](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)」(Oracle パブリッシャーの構成) をご覧ください。  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-change-security-settings-for-the-distribution-agent-for-a-push-subscription"></a>プッシュ サブスクリプションに対するディストリビューション エージェントのセキュリティ設定を変更するには  
  
1.  パブリッシャーの **[サブスクリプションのプロパティ - \<Subscription>]** ダイアログ ボックスでは、次の変更を加えることができます。  
  
    -   ディストリビューション エージェントを実行してディストリビューターへ接続するアカウントを変更するには、 **[エージェント プロセス アカウント]** 行をクリックしてから、その行のプロパティ ボタン (**[...]**) をクリックします。 **[ディストリビューション エージェント セキュリティ]** ダイアログ ボックスで、アカウントとパスワードを指定します。  
  
    -   ディストリビューション エージェントがサブスクライバーに接続するときのコンテキストを変更するには、 **[サブスクライバー接続]** 行をクリックしてから、その行のプロパティ ボタン (**[...]**) をクリックします。 **[接続情報の入力]** ダイアログ ボックスでコンテキストを指定します。  
  
         キュー更新サブスクリプションを使用する場合、ここで指定したコンテキストは、サブスクライバーに接続するためにキュー リーダー エージェントでも使用されます。  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-change-security-settings-for-the-distribution-agent-for-a-pull-subscription"></a>プル サブスクリプションに対するディストリビューション エージェントのセキュリティ設定を変更するには  
  
1.  サブスクライバーの **[サブスクリプションのプロパティ - \<Subscription>]** ダイアログ ボックスでは、次の変更を加えることができます。  
  
    -   ディストリビューション エージェントを実行してサブスクライバーへ接続するアカウントを変更するには、 **[エージェント プロセス アカウント]** 行をクリックしてから、その行のプロパティ ボタン (**[...]**) をクリックします。 **[ディストリビューション エージェント セキュリティ]** ダイアログ ボックスで、アカウントとパスワードを指定します。  
  
         キュー更新サブスクリプションを使用する場合、ここで指定したコンテキストは、サブスクライバーに接続するためにキュー リーダー エージェントでも使用されます。  
  
    -   ディストリビューション エージェントがディストリビューターに接続するときのコンテキストを変更するには、 **[ディストリビューター接続]** 行をクリックしてから、その行のプロパティ ボタン (**[...]**) をクリックします。 **[接続情報の入力]** ダイアログ ボックスでコンテキストを指定します。  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-change-security-settings-for-the-merge-agent-for-a-push-subscription"></a>プッシュ サブスクリプションに対するマージ エージェントのセキュリティ設定を変更するには  
  
1.  パブリッシャーの **[サブスクリプションのプロパティ - \<Subscription>]** ダイアログ ボックスでは、次の変更を加えることができます。  
  
    -   マージ エージェントを実行してパブリッシャーおよびディストリビューターへ接続するアカウントを変更するには、 **[エージェント プロセス アカウント]** 行をクリックしてから、その行のプロパティ ボタン (**[...]**) をクリックします。 **[マージ エージェント セキュリティ]** ダイアログ ボックスで、アカウントとパスワードを指定します。  
  
    -   マージ エージェントがサブスクライバーに接続するときのコンテキストを変更するには、 **[サブスクライバー接続]** 行をクリックしてから、その行のプロパティ ボタン (**[...]**) をクリックします。 **[接続情報の入力]** ダイアログ ボックスでコンテキストを指定します。  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-change-security-settings-for-the-merge-agent-for-a-pull-subscription"></a>プル サブスクリプションに対するマージ エージェントのセキュリティ設定を変更するには  
  
1.  サブスクライバーの **[サブスクリプションのプロパティ - \<Subscription>]** ダイアログ ボックスでは、次の変更を加えることができます。  
  
    -   マージ エージェントを実行してサブスクライバーへ接続するアカウントを変更するには、 **[エージェント プロセス アカウント]** 行をクリックしてから、その行のプロパティ ボタン (**[...]**) をクリックします。 **[マージ エージェント セキュリティ]** ダイアログ ボックスで、アカウントとパスワードを指定します。  
  
    -   マージ エージェントがパブリッシャーおよびディストリビューターに接続するときのコンテキストを変更するには、 **[パブリッシャー接続]** 行をクリックしてから、その行のプロパティ ボタン (**[...]**) をクリックします。 **[接続情報の入力]** ダイアログ ボックスでコンテキストを指定します。  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-change-the-account-under-which-the-queue-reader-agent-runs"></a>キュー リーダー エージェントを実行するアカウントを変更するには  
  
1.  **[ディストリビューターのプロパティ - \<Distributor>]** ダイアログ ボックスの **[全般]** ページで、ディストリビューション データベースの横にあるプロパティ ボタン (**…**) をクリックします。  
  
2.  **[ディストリビューション データベースのプロパティ - \<Database>]** ダイアログ ボックスで、**[エージェント プロセス アカウント]** テキスト ボックスの横にある **[セキュリティ設定]** ボタンをクリックします。  
  
3.  **[キュー リーダー エージェントのセキュリティ]** ダイアログ ボックスで、エージェントを実行してディストリビューターへ接続するアカウントを指定します。  
  
    -   **[プロセス アカウント]** テキスト ボックスに新しい Windows アカウントを入力します。  
  
    -   **[パスワード]** テキスト ボックスと **[パスワードの確認入力]** テキスト ボックスに、新しい複雑なパスワードを入力します。  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  ディストリビューション データベースには、それぞれ 1 つのキュー リーダー エージェントがあります。 エージェントのセキュリティ設定を変更すると、このディストリビューション データベースを使用するすべてのパブリッシャーのすべてのパブリケーションの設定に影響が及びます。  
  
#### <a name="to-change-the-context-under-which-the-queue-reader-agent-makes-connections-to-the-publisher"></a>キュー リーダー エージェントがパブリッシャーに接続するときのコンテキストを変更するには  
  
1.  **[ディストリビューターのプロパティ - \<Distributor>]** ダイアログ ボックスの **[パブリッシャー]** ページで、パブリッシャーの横にあるプロパティ ボタン (**...**) をクリックします。  
  
2.  **[パブリッシャーへのエージェント接続]** セクションで、 **[エージェント接続モード]** オプションの **[エージェント プロセス アカウントを借用する]** または **[SQL Server 認証]** の値を指定します。 **[SQL Server 認証]**を指定する場合は、 **[ログイン]** および **[パスワード]**の値も入力します。  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  ディストリビューション データベースには、それぞれ 1 つのキュー リーダー エージェントがあります。 エージェントのセキュリティ設定を変更すると、このディストリビューション データベースを使用するすべてのパブリッシャーのすべてのパブリケーションの設定に影響が及びます。  
  
#### <a name="to-change-the-context-under-which-the-queue-reader-agent-makes-connections-to-the-subscriber"></a>キュー リーダー エージェントがサブスクライバーに接続するときのコンテキストを変更するには  
  
-   キュー リーダー エージェントは、ディストリビューション エージェントと同じ接続コンテキストをサブスクリプションに使用します。 詳細については、ディストリビューション エージェントに関する上記の手順を参照してください。  
  
#### <a name="to-change-security-settings-for-an-immediate-updating-pull-subscription"></a>即時更新プル サブスクリプションのセキュリティ設定を変更するには  
  
1.  サブスクライバーの **[サブスクリプションのプロパティ - \<Subscription>]** ダイアログ ボックスで、**[パブリッシャー接続]** 行をクリックしてから、その行のプロパティ ボタン (**…**) をクリックします。  
  
2.  **[接続情報の入力]** ダイアログ ボックスで、次のオプションのいずれかを選択します。  
  
    -   **[リンク サーバーまたはリモート サーバーからのログインを使用します]**。 [sp_addserver &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)、[sp_addlinkedserver &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)、[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、または他の方法を使用してサブスクライバ―とパブリッシャーの間にリモート サーバーまたはリンクされたサーバーを定義した場合は、このオプションを選択します。  
  
    -   **[次のログインとパスワードによる SQL Server 認証を使用する]**。 サブスクライバーとパブリッシャーの間でリモート サーバーまたはリンク サーバーを定義していない場合は、このオプションを選択します。 レプリケーションによってリンク サーバーが作成されます。 指定するアカウントは、パブリッシャーに既に存在している必要があります。  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
> [!NOTE]  
>  この手順により、サブスクライバーで変更が行われたときに、レプリケーション トリガーがサブスクライバーからパブリッシャーに接続するために使用する方法が変更されます。 ディストリビューション エージェントに関連付けられている設定を即時更新サブスクリプション用に変更することもできます。 詳細については、このトピックで既に説明した手順を参照してください。  
>   
>  この手順は、プル サブスクリプションにのみ当てはまります。 プッシュ サブスクリプションには、ストアド プロシージャ [sp_link_publication &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md) を使用します。  
  
#### <a name="to-change-the-password-for-the-administrative-connection-from-the-publisher-to-the-distributor"></a>パブリッシャーからディストリビューターへの管理接続に使用されているパスワードを変更するには  
  
1.  **[ディストリビューターのプロパティ - \<Distributor>]** ダイアログ ボックスの **[パブリッシャー]** ページで、**[パスワード]** テキスト ボックスと **[パスワードの確認入力]** テキスト ボックスに複雑なパスワードを入力します。  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
3.  **[パブリッシャーのプロパティ - \<Publisher>]** ダイアログ ボックスの **[全般]** ページで、**[パスワード]** テキスト ボックスと **[パスワードの確認入力]** テキスト ボックスに複雑なパスワードを入力します。  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
> [!IMPORTANT]  
>  可能な限り、次のすべての手順で、実行時にセキュリティ資格情報を入力するように求めるメッセージをユーザーに表示します。 スクリプト ファイルに資格情報を格納する場合は、不正アクセスを防ぐために、そのファイルをセキュリティで保護する必要があります。  
  
#### <a name="to-change-all-instances-of-a-stored-password-at-a-replication-server"></a>レプリケーション サーバーに格納されたパスワードのインスタンスをすべて変更するには  
  
1.  レプリケーション トポロジ内のサーバーの master データベースで、 [sp_changereplicationserverpasswords](../../../relational-databases/system-stored-procedures/sp-changereplicationserverpasswords-transact-sql.md)を実行します。 **@login** に、パスワードを変更する [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows アカウントまたは [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインを指定し、**@password** に、そのアカウントまたはログインの新しいパスワードを入力します。 これにより、トポロジ内の他のサーバーに接続すると、サーバーのすべてのエージェントで使用されるパスワードの各インスタンスが変更されます。  
  
    > [!NOTE]  
    >  ディストリビューターやサブスクライバーなど、トポロジ内の特定のサーバーへの接続に対するログインおよびパスワードのみを変更するには、 **@server**」を参照してください。  
  
2.  パスワードの更新が必要なレプリケーション トポロジ内の各サーバーで手順 1. を繰り返します。  
  
    > [!NOTE]  
    >  レプリケーション パスワードを変更したら、そのパスワードを使用する各エージェントを停止して再起動し、エージェントに対して変更を反映させる必要があります。  
  
#### <a name="to-change-security-settings-for-the-snapshot-agent"></a>スナップショット エージェントのセキュリティ設定を変更するには  
  
1.  パブリッシャーで、 [@publication](../../../relational-databases/system-stored-procedures/sp-helppublication-snapshot-transact-sql.md)を指定して **@publication**」を参照してください。 これにより、スナップショット エージェントの現在のセキュリティ設定が返されます。  
  
2.  パブリッシャーで、 [@publication](../../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md)を指定して **@publication** を実行します。  
  
    -   エージェントの実行時に使用する Windows アカウント、またはこのアカウントのパスワードだけを変更するには、 **@job_login** 」および「 **@job_password**」を参照してください。  
  
    -   パブリッシャーへの接続時に使用するセキュリティ モードを指定するには、 **@publisher_security_mode** オプションの **1** または **@publisher_security_mode**」を参照してください。  
  
    -   パブリッシャーへの接続時に使用するセキュリティ モードを **@publisher_security_mode** から **1** に変更する場合、またはこの接続に使用する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインを変更する場合は、 **@publisher_login** 」および「 **@publisher_password**」を参照してください。  
  
    > [!IMPORTANT]  
    >  リモート ディストリビューターを使用するパブリッシャーを構成する場合は、 *job_login* および *job_password*を含むすべてのパラメーターに指定された値がディストリビューターにプレーン テキストとして送信されます。 このストアド プロシージャを実行する前に、パブリッシャーとリモート ディストリビューターの間の接続を暗号化する必要があります。 詳細については、「[データベース エンジンへの暗号化接続の有効化 &#40;SQL Server 構成マネージャー&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)」を参照してください。  
  
#### <a name="to-change-security-settings-for-the-log-reader-agent"></a>ログ リーダー エージェントのセキュリティ設定を変更するには  
  
1.  パブリッシャーで、 [@publisher](../../../relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql.md)を指定して **@publisher**」を参照してください。 これにより、ログ リーダー エージェントの現在のセキュリティ設定が返されます。  
  
2.  パブリッシャーで、 [@publication](../../../relational-databases/system-stored-procedures/sp-changelogreader-agent-transact-sql.md)を指定して **@publication** を実行します。  
  
    -   エージェントの実行時に使用する Windows アカウント、またはこのアカウントのパスワードだけを変更するには、 **@job_login** 」および「 **@job_password**」を参照してください。  
  
    -   パブリッシャーへの接続時に使用するセキュリティ モードを指定するには、 **@publisher_security_mode** オプションの **1** または **@publisher_security_mode**」を参照してください。  
  
    -   パブリッシャーへの接続時に使用するセキュリティ モードを **@publisher_security_mode** から **1** に変更する場合、またはこの接続に使用する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインを変更する場合は、 **@publisher_login** 」および「 **@publisher_password**」を参照してください。  
  
    > [!NOTE]  
    >  エージェントのログインまたはパスワードを変更した後、変更を有効にするには、エージェントを停止して再起動する必要があります。  
  
    > [!IMPORTANT]  
    >  リモート ディストリビューターを使用するパブリッシャーを構成する場合は、 *job_login* および *job_password*を含むすべてのパラメーターに指定された値がディストリビューターにプレーン テキストとして送信されます。 このストアド プロシージャを実行する前に、パブリッシャーとリモート ディストリビューターの間の接続を暗号化する必要があります。 詳細については、「[データベース エンジンへの暗号化接続の有効化 &#40;SQL Server 構成マネージャー&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)」を参照してください。  
  
#### <a name="to-change-security-settings-for-the-distribution-agent-for-a-push-subscription"></a>プッシュ サブスクリプションに対するディストリビューション エージェントのセキュリティ設定を変更するには  
  
1.  パブリッシャーのパブリケーション データベースで、 [@publication](../../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)を指定して **@publication** 」および「 **@subscriber**」を参照してください。 これにより、ディストリビューターで実行されるディストリビューション エージェントのセキュリティ設定を含むサブスクリプションのプロパティが返されます。  
  
2.  パブリッシャーのパブリケーション データベースで、 [sp_changesubscription](../../../relational-databases/system-stored-procedures/sp-changesubscription-transact-sql.md)を指定して **@publication**、 **@subscriber**、 **@subscriber_db**を指定し、 **@article** または **@article**を、 **@property**にセキュリティ プロパティの名前を、 **@value**」を参照してください。  
  
3.  次のセキュリティ プロパティから変更するものに対してそれぞれ手順 2. を繰り返します。  
  
    -   エージェントの実行時に使用する Windows アカウントまたはそのアカウントのパスワードだけを変更するには、 **@property** または **@property** を、 **@value**」を参照してください。 アカウント自体を変更する場合は、 **@property** または **@property** を、 **@value**」を参照してください。  
  
    -   サブスクライバーへの接続時に使用するセキュリティ モードを変更するには、 **@property** または **@property** を、 **@publisher_security_mode** に **1** (Windows 統合認証) または **@value**」を参照してください。  
  
    -   サブスクライバーのセキュリティ モードを SQL Server 認証に変更する場合、または SQL Server 認証のログイン情報を変更する場合は、 **@property** または **@property** を、 **@value**」を参照してください。 **@property** に **subscriber_login** を、**@value** に新しいログインを指定して、手順 2 を繰り返します。  
  
    > [!NOTE]  
    >  エージェントのログインまたはパスワードを変更した後、変更を有効にするには、エージェントを停止して再起動する必要があります。  
  
    > [!IMPORTANT]  
    >  リモート ディストリビューターを使用するパブリッシャーを構成する場合は、 **distrib_job_login** および **distrib_job_password**を含むすべてのプロパティに指定された値がディストリビューターにプレーン テキストとして送信されます。 このストアド プロシージャを実行する前に、パブリッシャーとリモート ディストリビューターの間の接続を暗号化する必要があります。 詳細については、「[データベース エンジンへの暗号化接続の有効化 &#40;SQL Server 構成マネージャー&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)」を参照してください。  
  
#### <a name="to-change-security-settings-for-the-distribution-agent-for-a-pull-subscription"></a>プル サブスクリプションに対するディストリビューション エージェントのセキュリティ設定を変更するには  
  
1.  サブスクライバーで、 [@publication](../../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md)を指定して **@publication**」を参照してください。 これにより、サブスクライバーで実行されるディストリビューション エージェントのセキュリティ設定を含むサブスクリプションのプロパティが返されます。  
  
2.  サブスクライバーのサブスクリプション データベースで、 [@publisher](../../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md)を指定して **@publisher**、 **@publisher_db**、 **@publication**を、 **@property**にセキュリティ プロパティの名前を、 **@value**」を参照してください。  
  
3.  次のセキュリティ プロパティから変更するものに対してそれぞれ手順 2. を繰り返します。  
  
    -   エージェントの実行時に使用する Windows アカウントまたはそのアカウントのパスワードだけを変更するには、 **@property** または **@property** を、 **@value**」を参照してください。 アカウント自体を変更する場合は、 **@property** または **@property** を、 **@value**」を参照してください。  
  
    -   ディストリビューターへの接続時に使用するセキュリティ モードを変更するには、 **@property** または **@property** を、 **@publisher_security_mode** に **1** (Windows 統合認証) または **@value**」を参照してください。  
  
    -   ディストリビューターのセキュリティ モードを SQL Server 認証に変更する場合、または SQL Server 認証のログイン情報を変更する場合は、 **@property** または **@property** を、 **@value**」を参照してください。 **@property** に **distributor_login** を、**@value** に新しいログインを指定して、手順 2 を繰り返します。  
  
    > [!NOTE]  
    >  エージェントのログインまたはパスワードを変更した後、変更を有効にするには、エージェントを停止して再起動する必要があります。  
  
#### <a name="to-change-security-settings-for-the-merge-agent-for-a-push-subscription"></a>プッシュ サブスクリプションに対するマージ エージェントのセキュリティ設定を変更するには  
  
1.  パブリッシャーのパブリケーション データベースで、 [@publication](../../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md)を指定して **@publication**、 **@subscriber**を指定して、 **@subscriber_db**」を参照してください。 これにより、ディストリビューターで実行されるマージ エージェントのセキュリティ設定を含むサブスクリプションのプロパティが返されます。  
  
2.  パブリッシャーのパブリケーション データベースで、 [@publication](../../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md)を指定して **@publication**、 **@subscriber**、 **@subscriber_db**を、 **@property**にセキュリティ プロパティの名前を、 **@value**」を参照してください。  
  
3.  次のセキュリティ プロパティから変更するものに対してそれぞれ手順 2. を繰り返します。  
  
    -   エージェントの実行時に使用する Windows アカウントまたはそのアカウントのパスワードだけを変更するには、 **@property** または **@property** を、 **@value**」を参照してください。 アカウント自体を変更する場合は、 **@property** または **@property** を、 **@value**」を参照してください。  
  
    -   サブスクライバーへの接続時に使用するセキュリティ モードを変更するには、 **@property** または **@property** を、 **@publisher_security_mode** に **1** (Windows 統合認証) または **@value**」を参照してください。  
  
    -   サブスクライバーのセキュリティ モードを SQL Server 認証に変更する場合、または SQL Server 認証のログイン情報を変更する場合は、 **@property** または **@property** を、 **@value**」を参照してください。 **@property** に **subscriber_login** を、**@value** に新しいログインを指定して、手順 2 を繰り返します。  
  
    -   パブリッシャーへの接続時に使用するセキュリティ モードを指定するには、 **@property** または **@property** を、 **@publisher_security_mode** に **1** (Windows 統合認証) または **@value**」を参照してください。  
  
    -   パブリッシャーのセキュリティ モードを SQL Server 認証に変更する場合、または SQL Server 認証のログイン情報を変更する場合は、 **@property** または **@property** を、 **@value**」を参照してください。 **@property** に **publisher_login** を、**@value** に新しいログインを指定して、手順 2 を繰り返します。  
  
    > [!NOTE]  
    >  エージェントのログインまたはパスワードを変更した後、変更を有効にするには、エージェントを停止して再起動する必要があります。  
  
    > [!IMPORTANT]  
    >  リモート ディストリビューターを使用してパブリッシャーを構成する場合、 **merge_job_login** および **merge_job_password**を含むすべてのプロパティに指定された値がディストリビューターにプレーン テキストとして送信されます。 このストアド プロシージャを実行する前に、パブリッシャーとリモート ディストリビューターの間の接続を暗号化する必要があります。 詳細については、「[データベース エンジンへの暗号化接続の有効化 &#40;SQL Server 構成マネージャー&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)」を参照してください。  
  
#### <a name="to-change-security-settings-for-the-merge-agent-for-a-pull-subscription"></a>プル サブスクリプションに対するマージ エージェントのセキュリティ設定を変更するには  
  
1.  サブスクライバーで、 [@publication](../../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md)を指定して **@publication**」を参照してください。 これにより、サブスクライバーで実行されるマージ エージェントのセキュリティ設定を含むサブスクリプションのプロパティが返されます。  
  
2.  サブスクライバーのサブスクリプション データベースで、 [@publisher](../../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md)を指定して **@publisher**、 **@publisher_db**、 **@publication**を、 **@property**にセキュリティ プロパティの名前を、 **@value**」を参照してください。  
  
3.  次のセキュリティ プロパティから変更するものに対してそれぞれ手順 2. を繰り返します。  
  
    -   エージェントの実行時に使用する Windows アカウントまたはそのアカウントのパスワードだけを変更するには、 **@property** または **@property** を、 **@value**」を参照してください。 When changing the account itself, repeat Step 2 specifying a value of **@property** または **@property** を、 **@value**」を参照してください。  
  
    -   ディストリビューターへの接続時に使用するセキュリティ モードを変更するには、 **@property** または **@property** を、 **@publisher_security_mode** に **1** (Windows 統合認証) または **@value**」を参照してください。  
  
    -   ディストリビューターのセキュリティ モードを SQL Server 認証に変更する場合、または SQL Server 認証のログイン情報を変更する場合は、 **@property** または **@property** を、 **@value**」を参照してください。 **@property** に **distributor_login** を、**@value** に新しいログインを指定して、手順 2 を繰り返します。  
  
    -   パブリッシャーへの接続時に使用するセキュリティ モードを指定するには、 **@property** または **@property** を、 **@publisher_security_mode** に **1** (Windows 統合認証) または **@value**」を参照してください。  
  
    -   パブリッシャーのセキュリティ モードを SQL Server 認証に変更する場合、または SQL Server 認証のログイン情報を変更する場合は、 **@property** または **@property** を、 **@value**」を参照してください。 **@property** に **publisher_login** を、**@value** に新しいログインを指定して、手順 2 を繰り返します。  
  
    > [!NOTE]  
    >  エージェントのログインまたはパスワードを変更した後、変更を有効にするには、エージェントを停止して再起動する必要があります。  
  
#### <a name="to-change-security-settings-for-the-snapshot-agent-to-generate-a-filtered-snapshot-for-a-subscriber"></a>サブスクライバーのフィルター選択されたスナップショットを生成する、スナップショット エージェントのセキュリティ設定を変更するには  
  
1.  パブリッシャーで、 [@publication](../../../relational-databases/system-stored-procedures/sp-helpdynamicsnapshot-job-transact-sql.md)を指定して **@publication**」を参照してください。 結果セットで、変更するサブスクライバーのパーティションの **job_name** の値を確認します。  
  
2.  パブリッシャーで、 [@publication](../../../relational-databases/system-stored-procedures/sp-changedynamicsnapshot-job-transact-sql.md)を指定して **@publication**に手順 1. で取得した値を、 **@dynamic_snapshot_jobname**に新しい値を、または **@job_password** および **@job_login** 」および「 **@job_password**」を参照してください。  
  
    > [!IMPORTANT]  
    >  リモート ディストリビューターを使用するパブリッシャーを構成する場合は、 *job_login* および *job_password*を含むすべてのパラメーターに指定された値がディストリビューターにプレーン テキストとして送信されます。 このストアド プロシージャを実行する前に、パブリッシャーとリモート ディストリビューターの間の接続を暗号化する必要があります。 詳細については、「[データベース エンジンへの暗号化接続の有効化 &#40;SQL Server 構成マネージャー&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)」を参照してください。  
  
#### <a name="to-change-security-settings-for-the-queue-reader-agent"></a>キュー リーダー エージェントのセキュリティ設定を変更するには  
  
1.  ディストリビューターで、 [sp_helpqreader_agent](../../../relational-databases/system-stored-procedures/sp-helpqreader-agent-transact-sql.md)を実行します。 これにより、キュー リーダー エージェントの実行時に使用される現在の Windows アカウントが返されます。  
  
    -   ディストリビューターで、 [@job_login](../../../relational-databases/system-stored-procedures/sp-changeqreader-agent-transact-sql.md)および **@job_login** 」および「 **@job_passwsord**」を参照してください。  
  
    > [!NOTE]  
    >  エージェントのログインまたはパスワードを変更した後、変更を有効にするには、エージェントを停止して再起動する必要があります。 ディストリビューション データベースには、それぞれ 1 つのキュー リーダー エージェントがあります。 エージェントのセキュリティ設定を変更すると、このディストリビューション データベースを使用するすべてのパブリッシャーのすべてのパブリケーションの設定に影響が及びます。  
  
2.  キュー リーダー エージェントは、サブスクリプションのディストリビューション エージェントと同じ接続コンテキストを使用して、サブスクライバーへの接続を作成します。  
  
#### <a name="to-change-security-mode-used-by-an-immediate-updating-subscriber-when-connecting-to-the-publisher"></a>パブリッシャーへの接続時に即時更新サブスクライバーで使用するセキュリティ モードを変更するには  
  
1.  サブスクライバー側のサブスクリプション データベースに対して、 [sp_link_publication](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md)を実行します。 **@publisher**、**@publication** を指定し、**@publisher_db** にパブリケーション データベース名を、**@security_mode** に次のいずれかの値を指定します。  
  
    -   **0** - パブリッシャーで更新を作成する場合に SQL Server  認証を使用します。 このオプションの場合、パブリッシャーで、 **@login** 」および「 **@password**」を参照してください。  
  
    -   **1** - パブリッシャーへの接続時にサブスクライバーで変更するユーザーのセキュリティ コンテキストを使用します。 このセキュリティ モードに関連する制限の詳細については、 [sp_link_publication](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md) のトピックを参照してください。  
  
    -   **2** - [sp_addlinkedserver &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md) を使って作成された既存のユーザー定義リンク サーバー ログインを使用します。  
  
#### <a name="to-change-the-password-for-a-remote-distributor"></a>リモート ディストリビューターのパスワードを変更するには  
  
1.  ディストリビューターのディストリビューション データベースで、 [@password](../../../relational-databases/system-stored-procedures/sp-changedistributor-password-transact-sql.md)にこのログインの新しいパスワードを指定して、 **@password**」を参照してください。  
  
    > [!IMPORTANT]  
    >  **distributor_admin** のパスワードを直接変更しないでください。  
  
2.  このリモート ディストリビューターを使用する各パブリッシャーで、 [@password](../../../relational-databases/system-stored-procedures/sp-changedistributor-password-transact-sql.md)に手順 1. のパスワードを指定して、 **@password**」を参照してください。  
  
##  <a name="RMOProcedure"></a> レプリケーション管理オブジェクト (RMO) の使用  
  
> [!IMPORTANT]  
>  可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 資格情報を保存する必要がある場合は、 [Windows .NET Framework に用意されている](http://go.microsoft.com/fwlink/?LinkId=34733) 暗号化サービス [!INCLUDE[msCoName](../../../includes/msconame-md.md)] を使用します。  
  
#### <a name="to-change-all-instances-of-a-password-stored-on-a-replication-server"></a>レプリケーション サーバーに格納されているパスワードのインスタンスをすべて変更するには  
  
1.  <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、レプリケーション サーバーへの接続を作成します。  
  
2.  手順 1 で作成した接続を使用して、<xref:Microsoft.SqlServer.Replication.ReplicationServer> クラスのインスタンスを作成します。  
  
3.  <xref:Microsoft.SqlServer.Replication.ReplicationServer.ChangeReplicationServerPasswords%2A> メソッドを呼び出します。 次のパラメーターを指定します。  
  
    -   *security_mode* - <xref:Microsoft.SqlServer.Replication.ReplicationSecurityMode> の値。パスワードのインスタンスをすべて変更する認証の種類を指定します。  
  
    -   *login* - パスワードのすべてのインスタンスを変更するために使用するログイン。  
  
    -   *password* - 新しいパスワード値。  
  
        > [!IMPORTANT]  
        >  可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 資格情報を保存する必要がある場合は、Windows .NET Framework に用意されている [暗号化サービス](http://go.microsoft.com/fwlink/?LinkId=34733) を使用します。  
  
        > [!NOTE]  
        >  固定サーバー ロール **sysadmin** のメンバー以外、このメソッドを呼び出すことはできません。  
  
4.  パスワードを更新する必要のある、レプリケーション トポロジ内のすべてのサーバーについて、手順 1. から手順 3. を繰り返します。  
  
#### <a name="to-change-security-settings-for-the-distribution-agent-for-a-push-subscription-to-a-transactional-publication"></a>ディストリビューション エージェントのセキュリティ設定をプッシュ サブスクリプション用からトランザクション パブリケーション用に変更するには  
  
1.  <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、パブリッシャーへの接続を作成します。  
  
2.  <xref:Microsoft.SqlServer.Replication.TransSubscription> クラスのインスタンスを作成します。  
  
3.  サブスクリプションの <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>、<xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>、<xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>、<xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> の各プロパティを設定し、手順 1 で作成した接続を <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに設定します。  
  
4.  <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、オブジェクトのプロパティを取得します。 このメソッドから **false**が返された場合、手順 3. で指定したサブスクリプションのプロパティが正しく定義されていないか、サブスクリプションが存在していません。  
  
5.  <xref:Microsoft.SqlServer.Replication.TransSubscription> のインスタンスに対して、次のいずれかまたは複数のセキュリティ プロパティを設定します。  
  
    -   エージェントの実行に使用する Windows アカウントの資格情報を変更するには、<xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A> の <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> フィールドと <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> フィールドを設定します。  
  
    -   エージェントがサブスクライバーとの接続に使用する認証の種類に Windows 統合認証を指定するには、<xref:Microsoft.SqlServer.Replication.Subscription.SubscriberSecurity%2A> プロパティの <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> フィールドを **true** に設定します。  
  
    -   エージェントがサブスクライバーとの接続に使用する認証の種類に SQL Server 認証を指定するには、<xref:Microsoft.SqlServer.Replication.Subscription.SubscriberSecurity%2A> プロパティの <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> フィールドを **false** に設定し、さらに、<xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> フィールドと <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> フィールドに対して、サブスクライバーのログイン資格情報を設定します。  
  
        > [!NOTE]  
        >  ディストリビューターに対するエージェント接続は、常に、<xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A> によって指定された Windows 資格情報を使用して確立されます。 このアカウントは、Windows 認証を使ってリモート接続を確立する際にも使用されます。  
  
6.  (省略可) <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> に **true** を指定した場合は、<xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドを呼び出してサーバーに変更をコミットします。 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> に **false** を指定した場合 (既定値)、変更は直ちにサーバーに送られます。  
  
#### <a name="to-change-security-settings-for-the-distribution-agent-for-a-pull-subscription-to-a-transactional-publication"></a>ディストリビューション エージェントのセキュリティ設定をプル サブスクリプション用からトランザクション パブリケーション用に変更するには  
  
1.  <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、サブスクライバーへの接続を作成します。  
  
2.  <xref:Microsoft.SqlServer.Replication.TransPullSubscription> クラスのインスタンスを作成します。  
  
3.  サブスクリプションの <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>、<xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>、<xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>、<xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> の各プロパティを設定し、<xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに対し、手順 1 で作成した接続を設定します。  
  
4.  <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、オブジェクトのプロパティを取得します。 このメソッドから **false**が返された場合、手順 3. で指定したサブスクリプションのプロパティが正しく定義されていないか、サブスクリプションが存在していません。  
  
5.  <xref:Microsoft.SqlServer.Replication.TransPullSubscription> のインスタンスに対して、次のいずれかまたは複数のセキュリティ プロパティを設定します。  
  
    -   エージェントの実行に使用する Windows アカウントの資格情報を変更するには、<xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A> の <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> フィールドと <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> フィールドを設定します。  
  
    -   エージェントがディストリビューターとの接続に使用する認証の種類に Windows 統合認証を指定するには、<xref:Microsoft.SqlServer.Replication.PullSubscription.DistributorSecurity%2A> プロパティの <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> フィールドを **true** に設定します。  
  
    -   エージェントがディストリビューターとの接続に使用する認証の種類に SQL Server 認証を指定するには、<xref:Microsoft.SqlServer.Replication.PullSubscription.DistributorSecurity%2A> プロパティの <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> フィールドを **false** に設定し、さらに、<xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> フィールドと <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> フィールドに対して、ディストリビューターのログイン資格情報を設定します。  
  
        > [!NOTE]  
        >  サブスクライバーに対するエージェント接続は、常に、<xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A> によって指定された Windows 資格情報を使用して確立されます。 このアカウントは、Windows 認証を使ってリモート接続を確立する際にも使用されます。  
  
6.  (省略可) <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> に **true** を指定した場合は、<xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドを呼び出してサーバーに変更をコミットします。 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> に **false** を指定した場合 (既定値)、変更は直ちにサーバーに送られます。  
  
#### <a name="to-change-security-settings-for-the-merge-agent-for-a-pull-subscription-to-a-merge-publication"></a>マージ エージェントのセキュリティ設定をプル サブスクリプション用からマージ パブリケーション用に変更するには  
  
1.  <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、サブスクライバーへの接続を作成します。  
  
2.  <xref:Microsoft.SqlServer.Replication.MergePullSubscription> クラスのインスタンスを作成します。  
  
3.  サブスクリプションの <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>、<xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>、<xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>、<xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> の各プロパティを設定し、<xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに対し、手順 1 で作成した接続を設定します。  
  
4.  <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、オブジェクトのプロパティを取得します。 このメソッドから **false**が返された場合、手順 3. で指定したサブスクリプションのプロパティが正しく定義されていないか、サブスクリプションが存在していません。  
  
5.  <xref:Microsoft.SqlServer.Replication.MergePullSubscription> のインスタンスに対して、次のいずれかまたは複数のセキュリティ プロパティを設定します。  
  
    -   エージェントの実行に使用する Windows アカウントの資格情報を変更するには、<xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A> の <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> フィールドと <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> フィールドを設定します。  
  
    -   エージェントがディストリビューターとの接続に使用する認証の種類に Windows 統合認証を指定するには、<xref:Microsoft.SqlServer.Replication.PullSubscription.DistributorSecurity%2A> プロパティの <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> フィールドを **true** に設定します。  
  
    -   エージェントがディストリビューターとの接続に使用する認証の種類に SQL Server 認証を指定するには、<xref:Microsoft.SqlServer.Replication.PullSubscription.DistributorSecurity%2A> プロパティの <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> フィールドを **false** に設定し、さらに、<xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> フィールドと <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> フィールドに対して、ディストリビューターのログイン資格情報を設定します。  
  
    -   エージェントがパブリッシャーとの接続に使用する認証の種類に Windows 統合認証を指定するには、<xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherSecurity%2A> プロパティの <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> フィールドを **true** に設定します。  
  
    -   エージェントがパブリッシャーとの接続に使用する認証の種類に SQL Server 認証を指定するには、<xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherSecurity%2A> プロパティの <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> フィールドを **false** に設定し、さらに、<xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> フィールドと <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> フィールドに対して、パブリッシャーのログイン資格情報を設定します。  
  
        > [!NOTE]  
        >  サブスクライバーに対するエージェント接続は、常に、<xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A> によって指定された Windows 資格情報を使用して確立されます。 このアカウントは、Windows 認証を使ってリモート接続を確立する際にも使用されます。  
  
6.  (省略可) <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> に **true** を指定した場合は、<xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドを呼び出してサーバーに変更をコミットします。 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> に **false** を指定した場合 (既定値)、変更は直ちにサーバーに送られます。  
  
#### <a name="to-change-security-settings-for-the-merge-agent-for-a-push-subscription-to-a-merge-publication"></a>マージ エージェントのセキュリティ設定をプッシュ サブスクリプション用からマージ パブリケーション用に変更するには  
  
1.  <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、パブリッシャーへの接続を作成します。  
  
2.  <xref:Microsoft.SqlServer.Replication.MergeSubscription> クラスのインスタンスを作成します。  
  
3.  サブスクリプションの <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>、<xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>、<xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>、<xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> の各プロパティを設定し、手順 1 で作成した接続を <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに設定します。  
  
4.  <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、オブジェクトのプロパティを取得します。 このメソッドから **false**が返された場合、手順 3. で指定したサブスクリプションのプロパティが正しく定義されていないか、サブスクリプションが存在していません。  
  
5.  <xref:Microsoft.SqlServer.Replication.MergeSubscription> のインスタンスに対して、次のいずれかまたは複数のセキュリティ プロパティを設定します。  
  
    -   エージェントの実行に使用する Windows アカウントの資格情報を変更するには、<xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A> の <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> フィールドと <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> フィールドを設定します。  
  
    -   エージェントがサブスクライバーとの接続に使用する認証の種類に Windows 統合認証を指定するには、<xref:Microsoft.SqlServer.Replication.Subscription.SubscriberSecurity%2A> プロパティの <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> フィールドを **true** に設定します。  
  
    -   エージェントがサブスクライバーとの接続に使用する認証の種類に SQL Server 認証を指定するには、<xref:Microsoft.SqlServer.Replication.Subscription.SubscriberSecurity%2A> プロパティの <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> フィールドを **false** に設定し、さらに、<xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> フィールドと <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> フィールドに対して、サブスクライバーのログイン資格情報を設定します。  
  
    -   エージェントがパブリッシャーとの接続に使用する認証の種類に Windows 統合認証を指定するには、<xref:Microsoft.SqlServer.Replication.MergeSubscription.PublisherSecurity%2A> プロパティの <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> フィールドを **true** に設定します。  
  
    -   エージェントがパブリッシャーとの接続に使用する認証の種類に SQL Server 認証を指定するには、<xref:Microsoft.SqlServer.Replication.MergeSubscription.PublisherSecurity%2A> プロパティの <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> フィールドを **false** に設定し、さらに、<xref:Microsoft.SqlServer.Replication.PublisherConnectionSecurityContext.SqlStandardLogin%2A> フィールドと <xref:Microsoft.SqlServer.Replication.PublisherConnectionSecurityContext.SqlStandardPassword%2A> フィールドに対して、パブリッシャーのログイン資格情報を設定します。  
  
        > [!NOTE]  
        >  ディストリビューターに対するエージェント接続は、常に、<xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A> によって指定された Windows 資格情報を使用して確立されます。 このアカウントは、Windows 認証を使ってリモート接続を確立する際にも使用されます。  
  
6.  (省略可) <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> に **true** を指定した場合は、<xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドを呼び出してサーバーに変更をコミットします。 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> に **false** を指定した場合 (既定値)、変更は直ちにサーバーに送られます。  
  
#### <a name="to-change-the-login-information-used-by-an-immediate-updating-subscriber-when-it-connects-to-the-transactional-publisher"></a>即時更新サブスクライバーがトランザクション パブリッシャーへの接続時に使用するログイン情報を変更するには  
  
1.  <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、サブスクライバーへの接続を作成します。  
  
2.  サブスクリプション データベースの <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> クラスのインスタンスを作成します。 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> に、手順 1 の <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.Name%2A> と <xref:Microsoft.SqlServer.Management.Common.ServerConnection> を設定します。  
  
3.  <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、オブジェクトのプロパティを取得します。 このメソッドから **false**が返された場合、手順 2. で指定したデータベースのプロパティが正しく定義されていないか、サブスクリプション データベースが存在していません。  
  
4.  <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.LinkPublicationForUpdateableSubscription%2A> メソッドを呼び出し、以下のパラメーターを渡します。  
  
    -   *Publisher* - パブリッシャーの名前。  
  
    -   *PublisherDB* - パブリケーション データベースの名前。  
  
    -   *Publication* - 即時更新サブスクライバーでサブスクライブしているパブリケーションの名前。  
  
    -   *Distributor* - ディストリビューターの名前。  
  
    -   *PublisherSecurity* - <xref:Microsoft.SqlServer.Replication.PublisherConnectionSecurityContext> オブジェクト。即時更新サブスクライバーがパブリッシャーに接続するときのセキュリティ モードと、その接続に必要なログイン資格情報を指定します。  
  
###  <a name="PShellExample"></a> 例 (RMO)  
 次の例では、指定されたログイン値をチェックし、該当する Windows ログイン、または、サーバー上のレプリケーションによって格納された SQL Server ログインを対象にすべてのパスワードを変更します。  
  
 [!code-cs[HowTo#rmo_ChangeServerPasswords](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_changeserverpasswords)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeServerPasswords](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_changeserverpasswords)]  
  
##  <a name="FollowUp"></a> フォロー アップ: レプリケーションのセキュリティ設定を変更した後  
 エージェントのログインまたはパスワードを変更した後、変更を有効にするには、エージェントを停止して再起動する必要があります。  
  
## <a name="see-also"></a>参照  
 [レプリケーション管理オブジェクトの概念](../../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [レプリケーション スクリプトのアップグレード &#40;レプリケーション Transact-SQL プログラミング&#41;](../../../relational-databases/replication/administration/upgrade-replication-scripts-replication-transact-sql-programming.md)   
 [レプリケーションのログインとパスワードの管理](../../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)   
 [レプリケーション エージェントのセキュリティ モデル](../../../relational-databases/replication/security/replication-agent-security-model.md)   
 [Replication Security Best Practices](../../../relational-databases/replication/security/replication-security-best-practices.md)   
 [セキュリティと保護 &#40;レプリケーション&#41;](../../../relational-databases/replication/security/security-and-protection-replication.md)   
 [Replication System Stored Procedures Concepts](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)  
  
  