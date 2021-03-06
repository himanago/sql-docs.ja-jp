---
title: バックアップ、復元、および SSIS カタログの移動 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: bf806aef-8556-48ab-aed5-e95de9a2204e
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 64d690c11a76d40e851a23374c568727e3f47a40
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48172782"
---
# <a name="backup-restore-and-move-the-ssis-catalog"></a>SSIS カタログのバックアップ、復元、および移動
  [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] SSISDB データベースが含まれています。 **SSISDB** カタログに格納されているオブジェクト、設定、および業務データを検査するには、SSISDB データベースのビューに対してクエリを実行します。 このトピックでは、データベースのバックアップと復元の手順について説明します。  
  
 **SSISDB** カタログは、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サーバーに配置したパッケージを格納します。 カタログの詳細については、「 [SSIS カタログ](catalog/ssis-catalog.md)」を参照してください。  
  
##  <a name="backup"></a> SSIS データベースをバックアップするには  
  
1.  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を開き、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のインスタンスに接続します。  
  
2.  BACKUP MASTER KEY Transact-SQL ステートメントを使用して、SSISDB データベースのマスター キーをバックアップします。 このキーは指定したファイルに格納されます。 ファイル内のマスター キーを暗号化するには、パスワードを使用します。  
  
     ステートメントの詳細については、「[BACKUP MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-master-key-transact-sql)」を参照してください。  
  
     次の例では、マスター キーが `c:\temp directory\RCTestInstKey` ファイルにエクスポートされます。 マスター キーの暗号化には、 `LS2Setup!` というパスワードが使用されます。  
  
    ```  
    backup master key to file = 'c:\temp\RCTestInstKey'  
           encryption by password = 'LS2Setup!'  
  
    ```  
  
3.  **の** [データベースのバックアップ] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]ダイアログ ボックスを使用して SSISDB データベースをバックアップします。 詳細については、「 [データベースをバックアップする方法 (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=231812)」を参照してください。  
  
4.  次の手順を実行して、##MS_SSISServerCleanupJobLogin## の CREATE LOGIN スクリプトを生成します。 詳細については、「[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql)」を参照してください。  
  
    1.  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のオブジェクト エクスプローラーで、**[セキュリティ]** ノードを展開し、**[ログイン]** ノードを展開します。  
  
    2.  **[##MS_SSISServerCleanupJobLogin##]** を右クリックし、 **[ログインをスクリプト化]** > **[CREATE]** > **[新しいクエリ エディター ウィンドウ]** の順にクリックします。  
  
5.  SSISDB カタログが作成されていない [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスに SSISDB データベースを復元する場合は、次の操作を行って、sp_ssis_startup の CREATE PROCEDURE スクリプトを生成します。 詳細については、「[CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql)」を参照してください。  
  
    1.  オブジェクト エクスプローラーで、**[データベース]** ノードを展開し、**[master]** > **[プログラミング]** > **[ストアド プロシージャ]** ノードの順に展開します。  
  
    2.  **[dbo.sp_ssis_startup]** を右クリックし、 **[ストアド プロシージャをスクリプト化]** > **[CREATE]** > **[新しいクエリ エディター ウィンドウ]** の順にクリックします。  
  
6.  SQL Server エージェントが起動したことを確認します。  
  
7.  SSISDB カタログが作成されていない [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスに SSISDB データベースを復元する場合は、次の操作を行って、SSIS サーバー メンテナンス ジョブのスクリプトを生成します。 SSISDB カタログが作成されると、スクリプトは [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントで自動的に作成されます。 このジョブは、保有期間外の操作ログのクリーンアップおよび古いバージョンのプロジェクトの削除に役立ちます。  
  
    1.  オブジェクト エクスプローラーで、 **[SQL Server エージェント]** ノードを展開し、 **[ジョブ]** ノードを展開します。  
  
    2.  SSIS サーバー メンテナンス ジョブを右クリックし、 **[ジョブをスクリプト化]** > **[CREATE]** > **[新しいクエリ エディター ウィンドウ]** の順にクリックします。  
  
### <a name="to-restore-the-ssis-database"></a>SSIS データベースを復元するには  
  
1.  SSISDB カタログが作成されていない [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスに SSISDB データベースを復元する場合は、sp_configure ストアド プロシージャを実行して、共通言語ランタイム (CLR) を有効にします。 詳細については、「[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)」と「[clr enabled サーバー構成オプション](http://go.microsoft.com/fwlink/?LinkId=231855)」を参照してください。  
  
    ```  
    use master   
           sp_configure 'clr enabled', 1  
           reconfigure  
  
    ```  
  
2.  SSISDB カタログが作成されていない [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスに SSISDB データベースを復元する場合は、非対称キーと非対称キーからのログインを作成し、UNSAFE 権限をログインに付与します。  
  
    ```  
    Create Asymmetric key MS_SQLEnableSystemAssemblyLoadingKey  
           FROM Executable File = 'C:\Program Files\Microsoft SQL Server\110\DTS\Binn\Microsoft.SqlServer.IntegrationServices.Server.dll'  
  
    ```  
  
     ログインを行うには Microsoft Win32 API などの制限付きのリソースへの追加アクセスが必要であるため、[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] CLR ストアド プロシージャでは、UNSAFE 権限をログインに付与する必要があります。 UNSAFE コード権限の要件の詳細については、「 [アセンブリの作成](../relational-databases/clr-integration/assemblies/creating-an-assembly.md)」を参照してください。  
  
    ```  
    Create Login MS_SQLEnableSystemAssemblyLoadingUser  
           FROM Asymmetric key MS_SQLEnableSystemAssemblyLoadingKey   
  
           Grant unsafe Assembly to MS_SQLEnableSystemAssemblyLoadingUser  
  
    ```  
  
3.  **の** [データベースの復元] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]ダイアログ ボックスを使用して、バックアップから SSISDB データベースを復元します。 詳細については、次の各トピックを参照してください。  
  
    -   [[データベースの復元] &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md)  
  
    -   [[データベースの復元] &#40;[ファイル] ページ&#41;](../relational-databases/backup-restore/restore-database-files-page.md)  
  
    -   [[データベースの復元] &#40;[オプション] ページ&#41;](../relational-databases/backup-restore/restore-database-options-page.md)  
  
4.  ##MS_SSISServerCleanupJobLogin##、sp_ssis_startup、および SSIS サーバー メンテナンス ジョブの「 [SSIS をバックアップするには](#backup) 」で作成したスクリプトを実行します。 SQL Server エージェントが起動したことを確認します。  
  
5.  次のステートメントを実行して、sp_ssis_startup プロシージャの自動実行を設定します。 詳細については、「[sp_procoption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql)」を参照してください。  
  
    ```  
    EXEC sp_procoption N'sp_ssis_startup','startup','on'  
    ```  
  
6.  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] の **[ログインのプロパティ]** ダイアログ ボックスを使用して、SSISDB ユーザーの ##MS_SSISServerCleanupJobUser## (SSISDB database) を ##MS_SSISServerCleanupJobLogin## にマップします。  
  
7.  次のいずれかの方法を使用して、マスター キーを復元します。 暗号化の詳細については、「 [暗号化階層](../relational-databases/security/encryption/encryption-hierarchy.md)」を参照してください。  
  
    -   **方法 1**  
  
         この方法は、データベース マスター キーのバックアップが実行済みで、マスター キーの暗号化に使用するパスワードがある場合に使用します。  
  
        ```  
               Restore master key from file = 'c:\temp\RCTestInstKey'  
               Decryption by password = 'LS2Setup!' -- 'Password used to encrypt the master key during SSISDB backup'  
               Encryption by password = 'LS3Setup!' -- 'New Password'  
               Force  
  
        ```  
  
        > [!NOTE]  
        >  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] サービス アカウントにバックアップ キー ファイルの読み取り権限があることを確認してください。  
  
        > [!NOTE]  
        >  データベース マスター キーがサービス マスター キーによって暗号化されていない場合、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] には次の警告メッセージが表示されます。 この警告メッセージは無視してください。  
        >   
        >  **現在のマスター キーは暗号化解除できません。FORCE オプションが指定されたので、エラーは無視されました。**  
        >   
        >  FORCE 引数は、現在のデータベース マスター キーが開いていない場合でも復元プロセスを続行するように指定します。 SSISDB カタログについては、データベースを復元するインスタンスでデータベース マスター キーが開いていないため、このメッセージが表示されます。  
  
    -   **方法 2**  
  
         この方法は、SSISDB の作成に使用した元のパスワードがある場合に使用します。  
  
        ```  
        open master key decryption by password = 'LS1Setup!' --'Password used when creating SSISDB'  
               Alter Master Key Add encryption by Service Master Key  
        ```  
  
8.  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] catalog.check_schema_version [を実行して、SSISDB カタログ スキーマと](/sql/integration-services/system-stored-procedures/catalog-check-schema-version)バイナリ (ISServerExec および SQLCLR アセンブリ) に互換性があるかどうかを確認します。  
  
9. SSISDB データベースが正常に復元されたことを確認するには、SSISDB カタログに対して、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サーバーに配置したパッケージの実行などの操作を実行します。 詳細については、「 [SQL Server Management Studio を使用した SSIS サーバーでのパッケージの実行](run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)」を参照してください。  
  
### <a name="to-move-the-ssis-database"></a>SSIS データベースを移動するには  
  
-   ユーザー データベースの移動の手順に従います。 詳細については、「 [ユーザー データベースの移動](../relational-databases/databases/move-user-databases.md)」を参照してください。  
  
     SSISDB データベースのマスター キーをバックアップしてバックアップ ファイルを保護していることを確認します。 詳細については、「 [SSIS データベースをバックアップするには](#backup)」を参照してください。  
  
     Integration Services (SSIS) 関連のオブジェクトが、SSISDB カタログが作成されていない新しい [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスに作成されていることを確認します。  
  
  
