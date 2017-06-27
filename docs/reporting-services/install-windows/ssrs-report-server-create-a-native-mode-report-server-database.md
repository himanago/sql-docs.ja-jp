---
title: "ネイティブ モード レポート サーバー データベース (SSRS 構成マネージャー) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/24/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- report servers [Reporting Services], databases
- databases [Reporting Services], creating
ms.assetid: 81b9f4ad-800b-4688-8b47-a5a83dc8ff10
caps.latest.revision: 12
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 1458fe51bc43c24904be30c5484f8829f8b45ebc
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---

# <a name="create-a-native-mode-report-server-database"></a>ネイティブ モードのレポート サーバー データベースの作成

[!INCLUDE[ssrs-appliesto-sql2016-preview](../../includes/ssrs-appliesto-sql2016-preview.md)]

ネイティブ モードの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースが内部ストレージとして使用されます。 データベースは必須で、パブリッシュされたレポート、モデル、共有データ ソース、セッション データ、リソース、およびサーバー メタデータの格納に使用されます。  

レポート サーバー データベースの作成や、接続文字列または資格情報の変更を行うには、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーの [データベース] ページにあるオプションを使用します。  
  
## <a name="when-to-create-or-configure-the-report-server-databases"></a>レポート サーバー データベースを作成または構成する場合  
 ファイルのみのモードでレポート サーバーをインストールした場合は、レポート サーバー データベースを作成および構成する必要があります。  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をネイティブ モードの既定の構成でインストールした場合、レポート サーバー データベースは、レポート サーバー インスタンスのインストール時に自動的に作成および構成されています。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを使用すると、セットアップによって自動的に構成された設定を表示または変更できます。  
  
##  <a name="rsdbrequirements"></a> 開始前の準備  
 レポート サーバー データベースの作成または構成は、複数の手順から成るプロセスです。 レポート サーバー データベースを作成する前に、次の項目をどのように指定するかを検討してください。  
  
 **データベース サーバーの選択**  
 サポートされている [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のバージョンとサポートされているエディションを「[レポート サーバー データベースの作成 &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-report-server-database.md)」で確認します。  
  
 **TCP/IP 接続の有効化**  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]の TCP/IP 接続を有効にします。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のエディションの中には、既定で TCP/IP が有効になっていないものもあります。 手順はこのトピックで説明します。  
  
 **ポートを開く [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**  
 リモート サーバーでファイアウォール ソフトウェアを使用している場合は、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] がリッスンするポートを開く必要があります。  
  
 **レポート サーバーの資格情報の決定**  
 レポート サーバーがレポート サーバー データベースに接続する方法を決定します。 資格情報の種類には、ドメイン ユーザー アカウント、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース ユーザー アカウント、およびレポート サーバー サービス アカウントがあります。  
  
 これらの資格情報は暗号化され、RSReportServer.config ファイルに格納されます。 レポート サーバーは、これらの資格情報を使用してレポート サーバー データベースに継続的に接続します。 Windows ユーザー アカウントまたはデータベース ユーザー アカウントを使用する場合は、既に存在するアカウントを指定してください。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーでは、ログインの作成と必要な権限の設定は実行されますが、アカウントは自動的に作成されません。 詳細については、「 [レポート サーバー データベース接続の構成 &#40;SSRS構成マネージャー&#41;](../../reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager.md)」で確認します。  
  
 **レポート サーバーの言語の決定**  
 レポート サーバーに対して指定する言語を選択します。 ユーザーが他言語バージョンのブラウザーを使用してサーバーに接続する場合でも、定義済みロールの名前、説明、および個人用レポート フォルダーは他の言語では表示されません。  
  
 **データベースを作成および準備するための資格情報の確認**  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンスでデータベースを作成する権限があるアカウントの資格情報を持っていることを確認します。 この資格情報は、レポート サーバー データベースおよび **RSExecRole**を作成するための一度だけの接続に使用されます。 ログインが存在しない場合は、レポート サーバーがデータベースに接続する際に使用するアカウント用にデータベース ユーザー ログインが作成されます。 ログインに使用している [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントで接続するか、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース ログインを入力することができます。  
  
### <a name="to-enable-access-to-a-remote-report-server-database"></a>リモートのレポート サーバー データベースにアクセスできるようにするには  
  
1.  リモートの [!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンスを使用している場合は、データベース サーバーにログオンして、TCP/IP 接続を確認するか有効にします。  
  
2.  **[スタート]**ボタンをクリックし、 **[すべてのプログラム]**、 **[Microsoft SQL Server]**、 **[構成ツール]**の順にポイントして、 **[SQL Server 構成マネージャー]**をクリックします。  
  
3.  **[SQL Server ネットワークの構成]**を開きます。  
  
4.  データベース インスタンスを選択します。  
  
5.  **[TCP/IP]** を右クリックし、 **[有効]**を選択します。  
  
6.  サービスを再起動します。  
  
7.  ファイアウォール ソフトウェアを開き、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がリッスンするポートを開きます。 既定のインスタンスの場合、このポートは通常、TCP/IP 接続のポート 1433 です。 Windows ファイアウォールの詳細については、 [オンライン ブックの「](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) データベース エンジン アクセスを有効にするための Windows ファイアウォールを構成する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 」を参照してください。  
  
### <a name="to-create-a-local-report-server-database"></a>ローカルのレポート サーバー データベースを作成するには  
  
1.  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを起動し、データベースを作成するレポート サーバー インスタンスに接続します。 詳細については、「 [Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)」で確認します。  
  
2.  [データベース] ページの **[データベースの変更]**を選択します。  
  
3.  **[新しいレポート サーバー データベースを作成する]**を選択し、 **[次へ]**を選択します。  
  
4.  レポート サーバー データベースの作成およびホストに使用する [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続します。  
  
    1.  使用する [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンス名を入力します。 使用可能であれば、既定のインスタンスとして実行されているローカルの [!INCLUDE[ssDE](../../includes/ssde-md.md)] がウィザードに表示されます。 使用可能でない場合は、使用するサーバーとインスタンスの名前を入力する必要があります。 名前付きインスタンスは、この形式で指定された: \<servername >\\< instancename\>です。  
  
    2.  レポート サーバー データベースを作成する目的で [!INCLUDE[ssDE](../../includes/ssde-md.md)] に一度だけ接続するために使用される資格情報を入力します。 この資格情報の使用方法の詳細については、このトピックの「 [開始前の準備](#rsdbrequirements) 」を参照してください。  
  
    3.  **[接続テスト]** を選択して、サーバーへの接続を検証します。  
  
    4.  [ **次へ**] を選択します。  
  
5.  データベースの作成に使用するプロパティを指定します。 このプロパティの使用方法の詳細については、このトピックの「 [開始前の準備](#rsdbrequirements) 」を参照してください。  
  
    1.  レポート サーバー データベースの名前を入力します。 プライマリ データベースと共に、一時データベースが作成されます。 データベースの使用方法が判断できるようなわかりやすい名前を使用することを検討してください。 指定した名前は、データベースの有効期間を通して使用されます。 作成後にレポート サーバー データベースの名前を変更することはできません。  
  
    2.  ロールの定義および個人用レポートの表示に使用する言語を選択します。  
  
    3.  [レポート サーバー モード] は常に **[ネイティブ]**に設定されます。  
  
    4.  [ **次へ**] を選択します。  
  
6.  レポート サーバーがレポート サーバー データベースに接続する際に使用する資格情報を指定します。  
  
    1.  認証の種類を指定します。  
  
         定義済みの **データベース ログインを使用して接続する場合は、** [データベース資格情報] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を選択します。 レポート サーバーが別のドメイン、信頼されていないドメイン、またはファイアウォールの背後のコンピューター上に存在する場合は、データベース資格情報を使用することをお勧めします。  
  
         最低限の特権のみを持ち、コンピューターおよびデータベース サーバーにログオンする権限のあるドメイン ユーザー アカウントを持っている場合は、 **[Windows 資格情報]** を選択します。  
  
         レポート サーバーの接続にレポート サーバーのサービス アカウントを使用する場合は、 **[サービス資格情報]** を選択します。 このオプションを指定すると、サーバーは統合セキュリティを使用して接続し、資格情報は暗号化されませんし、保存もされません。  
  
    2.  [ **次へ**] を選択します。  
  
7.  [概要] ページの情報で設定が正しいことを確認し、 **[次へ]**を選択します。  
  
8.  [レポート サーバー URL] ページまたは [レポート マネージャー URL] ページで URL を選択し、接続を確認します。 このテストが成功するように URL を定義する必要があります。 レポート サーバー データベースの接続が有効な場合は、ブラウザー ウィンドウにレポート サーバーのフォルダー階層またはレポート マネージャーが表示されます。 詳細については、 [オンライン ブックの「](../../reporting-services/install-windows/verify-a-reporting-services-installation.md) Reporting Services のインストール状態の検証 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 」を参照してください。  

## <a name="change-database-credentials"></a>データベース資格情報の変更

[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャー ツールの資格情報の変更ウィザードを使用して、レポート サーバーがレポート サーバー データベースへの接続に使用するアカウントを再構成することができます。 資格情報を変更すると、構成マネージャーによって、レポート サーバーで使用中のレポート サーバー データベースのデータベース サーバー上のすべての権限とデータベース ログイン情報が更新されます。 

1.  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを起動し、データベースを作成するレポート サーバー インスタンスに接続します。 詳細については、「 [Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)」で確認します。  
  
2.  [データベース] ページの **[資格情報の変更]**を選択します。 

3.  レポート サーバー データベースの作成およびホストに使用する [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続します。  
  
    1.  レポート サーバー データベースを作成する目的で [!INCLUDE[ssDE](../../includes/ssde-md.md)] に一度だけ接続するために使用される資格情報を入力します。 この資格情報の使用方法の詳細については、このトピックの「 [開始前の準備](#rsdbrequirements) 」を参照してください。  
  
    2.  **[接続テスト]** を選択して、サーバーへの接続を検証します。  
  
    3.  [ **次へ**] を選択します。  

4.  レポート サーバーがレポート サーバー データベースに接続する際に使用する資格情報を指定します。  
  
    1.  認証の種類を指定します。  
  
         定義済みの **データベース ログインを使用して接続する場合は、** [データベース資格情報] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を選択します。 レポート サーバーが別のドメイン、信頼されていないドメイン、またはファイアウォールの背後のコンピューター上に存在する場合は、データベース資格情報を使用することをお勧めします。  
  
         最低限の特権のみを持ち、コンピューターおよびデータベース サーバーにログオンする権限のあるドメイン ユーザー アカウントを持っている場合は、 **[Windows 資格情報]** を選択します。  
  
         レポート サーバーの接続にレポート サーバーのサービス アカウントを使用する場合は、 **[サービス資格情報]** を選択します。 このオプションを指定すると、サーバーは統合セキュリティを使用して接続し、資格情報は暗号化されませんし、保存もされません。  
  
    2.  [ **次へ**] を選択します。 

5. 設定を確認し、 **[次へ]**を選択します。

6. 変更を行ってから、 **[完了]**を選択します。

## <a name="next-steps"></a>次の手順

[レポート サーバー データベース接続を構成します。](../../reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
[Reporting Services ネイティブ モードのレポート サーバーの管理](../../reporting-services/report-server/manage-a-reporting-services-native-mode-report-server.md)   
[Reporting Services 構成マネージャー](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)  

他に質問しますか。 [Reporting Services のフォーラムで質問してみてください。](http://go.microsoft.com/fwlink/?LinkId=620231)