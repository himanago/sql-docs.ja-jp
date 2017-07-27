---
title: "SQL Server 2017 の各エディションとサポートされている機能 | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
- SQL2017_New_Updated
ms.date: 07/14/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- server-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Enterprise Edition [SQL Server]
- Developer Edition [SQL Server]
- 32-bit vs. 64-bit editions [SQL Server]
- default components
- Workgroup Edition [SQL Server]
- Internet servers [SQL Server]
- installing SQL Server, components
- Setup [SQL Server], components
- SQL Server, editions
- SQL Server, components
- client/server applications [SQL Server]
- editions [SQL Server]
- versions [SQL Server]
- Setup [SQL Server], editions
- SQL Server Installation Wizard
- components [SQL Server]
- Standard Edition [SQL Server]
- 64-bit edition [SQL Server]
- IIS [SQL Server]
- installing SQL Server, editions
- editions [SQL Server], about edition options
- Setup [SQL Server]
ms.assetid: 
caps.latest.revision: 121
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 6aa73e749d4f308265dfe27a160802c15a391a3e
ms.openlocfilehash: 6c17972f863043a53bf60b6c814aaac0c3c38d51
ms.contentlocale: ja-jp
ms.lasthandoff: 07/17/2017

---
# <a name="editions-and-supported-features-of-sql-server-2017"></a>SQL Server 2017 の各エディションとサポートされている機能

<!---[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]--->

このトピックでは、SQL Server 2017 のさまざまなエディションでサポートされている機能の詳細を説明します。 

以前のバージョンについては、以下を参照してください。

* [SQL Server 2016](editions-and-components-of-sql-server-2016.md)  
* [SQL Server 2014](http://msdn.microsoft.com/library/cc645993(v=sql.120).aspx)

>[!NOTE]
>この記事に記載した情報はすべて SQL Server 2017 の暫定リリースに適用されるため、変更される可能性があります。 
  
インストールの前提条件は、アプリケーションのニーズによって異なります。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] にはさまざまなエディションがあり、組織や個人の独自のパフォーマンス、ランタイム、および価格に関する要件に対応できます。 インストールする [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] コンポーネントは、ユーザーの特定の要件によっても異なります。 この後のセクションでは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の最適なエディションおよびコンポーネントを選択する方法について説明します。  

180 日の試用期間中、SQL Server Evaluation Edition をご利用いただけます。  
  
最新のリリース ノートと新機能については、以下の情報を参照してください。
- [SQL Server 2017 リリース ノート](../sql-server/sql-server-2017-release-notes.md)
- [SQL Server 2017 年 1 の新機能](../sql-server/what-s-new-in-sql-server-2017.md)

### <a name="try-sql-server"></a>SQL Server を実行してください。    
    
> [![Evaluation Center からダウンロードする](../analysis-services/media/download.png)](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2017-ctp/) **[Evaluation Center から SQL Server 2017 CTP をダウンロードする](https://www.microsoft.com/evalcenter/evaluate-sql-server-2017-ctp/)**    

<!---    
> ![Azure Virtual Machine small](../analysis-services/media/azure-virtual-machine-small.png) **[Spin up a Virtual Machine with SQL Server 2016 already installed](https://azuremarketplace.microsoft.com/marketplace/apps/Microsoft.SQL2016SP1-WS2016?tab=Overview?wt.mc_id=sqL16_vm)**   
--->

## <a name="includessnoversionincludesssnoversion-mdmd-editions"></a>[!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)] のエディション  
 次の表で、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のエディションについて説明します。 
  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エディション|定義|  
|---------------------------------------|----------------|  
|Enterprise|プレミアム製品である [!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)] Enterprise Edition は、非常に優れたパフォーマンス、無制限の仮想化、およびエンド ツー エンドのビジネス インテリジェンスを備えた包括的なハイエンド データセンター機能を提供することで、ミッション クリティカルなワークロードのための高水準のサービス レベルを実現し、エンド ユーザーがデータの意味を理解できるようにします。|  
|Standard|[!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)] Standard Edition は、企業部門や小規模組織がアプリケーションを実行するための基本的なデータ管理/ビジネス インテリジェンス データベースを提供し、内部設置型およびクラウド用の一般的な開発ツールをサポートすることで、最小限の IT リソースでデータベースを効果的に管理することを可能にします。|  
|Web|[!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)] Web Edition は、大小さまざまな規模の Web 資産に対応できるスケーラビリティ、経済性、および管理性を備えた、Web ホスティング企業および Web VAP 向けの総保有コストの低いオプションです。|  
|開発者|開発者は、[!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)] Developer Edition を使用して、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]上で動作するあらゆる種類のアプリケーションを開発できます。 このエディションには Enterprise Edition の機能がすべて含まれていますが、実稼動サーバーとして使用するのではなく、開発およびテスト システムとしての利用に対してライセンスが供与されます。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Developer は、<br />                [!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)] をビルドし、アプリケーションをテストするユーザーに適しています。|  
|Express Edition|Express Edition はエントリレベルの無料のデータベースで、学習や、デスクトップおよび小規模サーバー データ ドリブン アプリケーションの構築などに適しています。 このエディションは、独立系ソフトウェア ベンダー、開発者、クライアント アプリケーションを趣味で開発する開発者などに最適です。 さらに高度なデータベース機能が必要な場合には、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Express を [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の他の上位バージョンにシームレスにアップグレードできます。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Express LocalDB は、Express の簡易バージョンです。Express のプログラミング機能をすべて備えながら、ユーザー モードで実行でき、前提条件が少なく構成不要の高速インストールが可能です。|  
  
## <a name="using-includessnoversionincludesssnoversion-mdmd-with-an-internet-server"></a>[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] とインターネット サーバーの使用  
 インターネット インフォメーション サービス (IIS) を実行するサーバーなどのインターネット サーバーでは、一般に [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] クライアント ツールをインストールします。 クライアント ツールには、アプリケーションが [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスに接続する際に使用するクライアント接続コンポーネントが含まれています。  
  
>[!NOTE]
>IIS を実行しているコンピューターに [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスをインストールすることは可能ですが、通常はサーバー コンピューターが 1 台の小規模 Web サイトの場合に行います。 ほとんどの Web サイトでは、その中層 IIS システムが 1 つまたはクラスター構成の複数サーバーに配置され、データベースは 1 つの独立したサーバーまたは連合構成の複数サーバーに配置されます。  
  
## <a name="using-includessnoversionincludesssnoversion-mdmd-with-clientserver-applications"></a>[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] とクライアント/サーバー アプリケーションの使用  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のクライアント コンポーネントだけを、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のインスタンスに直接接続するクライアント/サーバー アプリケーションを実行するコンピューターにインストールできます。 クライアント コンポーネントをインストールすることは、データベース サーバー上にある [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスを管理する場合、または [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] アプリケーションを開発しようとしている場合にも適切なオプションです。  
  
 クライアント ツールをインストールするオプションを選択すると、下位互換コンポーネント、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 、接続コンポーネント、管理ツール、ソフトウェア開発キット、 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]オンライン ブック コンポーネントなどの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 機能がインストールされます。 詳細については、次を参照してください。 [SQL Server インストール](../database-engine/install-windows/install-sql-server.md)です。  
  
## <a name="deciding-among-includessnoversionincludesssnoversion-mdmd-components"></a>[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] コンポーネントの決定  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインストールに含めるコンポーネントを選択するには、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]インストール ウィザードの [機能の選択] ページを使用します。 既定では、ツリーの中に、選択されている機能はありません。  
  
 以下の表の情報を参照し、ニーズに最も合う機能を判断してください。  
  
|サーバー コンポーネント|Description|  
|-----------------------|-----------------|  
|[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]|[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] には [!INCLUDE[ssDE](../includes/ssde-md.md)]が含まれています。これは、データの格納、処理、およびセキュリティ保護、レプリケーション、フルテキスト検索、リレーショナルおよび XML データを管理するツール、データベース内分析機能の統合、および Hadoop とその他の異種データ ソースにアクセスするための Polybase 統合、および [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) サーバー用のコア サービスです。|  
|[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]|[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] には、オンライン分析処理 (OLAP) アプリケーションおよびデータ マイニング アプリケーションを作成および管理するためのツールが含まれます。|  
|[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]|[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] には、表形式、マトリックス形式、グラフィカル形式、および自由形式のレポートを作成、管理、配置するためのサーバー コンポーネントとクライアント コンポーネントが含まれます。 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] は、レポート アプリケーション開発用の拡張可能プラットフォームとしても使用できます。|  
|[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]|[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] は、データを移動、コピー、変換するためのグラフィカル ツールおよびプログラミング可能なオブジェクトのセットです。 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] 用の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)](DQS) コンポーネントも含まれています。|  
|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] (MDS) は、マスター データ管理のための [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ソリューションです。 MDS は、あらゆるドメイン (製品、顧客、アカウント) を管理するように構成できます。MDS には、データの管理に使用できる [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] のほかに、階層、きめ細かいセキュリティ、トランザクション、データのバージョン管理、およびビジネス ルールが含まれています。|  
|Machine Learning Services (データベース内)|Machine Learning Services (データベース内) は、エンタープライズ データ ソースを使用する分散型のスケーラブルな機械学習ソリューションをサポートします。 SQL Server 2016 では、R 言語がサポートされていました。 SQL Server 2017 では、R と Python がサポートされています。|
|Machine Learning Server (スタンドアロン)|Machine Learning Server (スタンドアロン) では、Linux、Hadoop、Teradata などの複数のエンタープライズ データ ソースを使用する分散型のスケーラブルな機械学習ソリューションを複数のプラットフォームに配置できます。 SQL Server 2016 では、R 言語がサポートされていました。 SQL Server 2017 では、R と Python がサポートされています。|

  
|管理ツール|Description|  
|----------------------|-----------------|  
|[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]|[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のコンポーネントを構成、管理、開発し、それらのコンポーネントへアクセスするための統合環境です。 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] では、すべてのスキル レベルの開発者と管理者が [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]を使用できます。<br /><br /> ダウンロードしてインストールする <br />                [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] (「  [SQL Server Management Studio (SSMS) のダウンロード](http://msdn.microsoft.com/library/mt238290.aspx)|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 構成マネージャー|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 構成マネージャーを使用して、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] サービス、サーバー プロトコル、クライアント プロトコル、およびクライアントの別名に関する基本的な構成管理を行います。|  
|[!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]|[!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] には、 [!INCLUDE[ssDE](../includes/ssde-md.md)] または [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]のインスタンスを監視するためのグラフィカル ユーザー インターフェイスが備わっています。|  
|[!INCLUDE[ssDE](../includes/ssde-md.md)] チューニング アドバイザー|[!INCLUDE[ssDE](../includes/ssde-md.md)] チューニング アドバイザーは、最適なインデックスのセット、インデックス付きビュー、およびパーティションの作成に役立ちます。|  
|Data Quality クライアント|DQS サーバーに接続し、データ クレンジング操作を実行するための、非常にシンプルで直感的なグラフィカル ユーザー インターフェイスを備えています。 データ クレンジング操作の際に行われるさまざまな処理を一元的に監視することもできます。|  
|[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]|[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] は、ビジネス インテリジェンス コンポーネント ( [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]) のソリューションをビルドするための IDE です。<br /><br /> (以前の Business Intelligence Development Studio)。<br /><br /> [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] には、Visual Studio 内で [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] プラットフォーム (社内および社外の両方) のデータベース設計を行うデータベース開発者用の統合環境である "データベース プロジェクト" も含まれます。 データベース開発者は、強化された Visual Studio のサーバー エクスプローラーを使用して、データベース オブジェクトおよびデータの作成または編集、クエリの実行を簡単に行うことができます。|  
|接続コンポーネント|クライアントとサーバー間の通信用コンポーネント、および DB-Library、ODBC、OLE DB 用のネットワーク ライブラリをインストールします。|  
  
|ドキュメント|Description|  
|-------------------|-----------------|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] オンライン ブック|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の主要マニュアル。| 

**Developer Edition と Evaluation Edition**   
Developer Edition と Evaluation Edition でサポートされている機能については、下の表に記載されている SQL Server Enterprise Edition の機能をご覧ください。

Developer edition はの 1 つのみのクライアントをサポートするために引き続き[SQL Server Distributed Replay](../tools/distributed-replay/sql-server-distributed-replay.md)です。 
  
##  <a name="Cross-BoxScaleLimits"></a> スケールの制限  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express| 
|-------------|----------------|--------------|---------|------------------------------------|------------------------|
|1 つのインスタンスで使用される最大計算容量 - [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]<sup>1</sup>|オペレーティング システムの最大容量|4 ソケットまたは 24 コアのいずれか小さいほうに制限|4 ソケットまたは 16 コアのいずれか小さいほうに制限|1 ソケットまたは 4 コアのいずれか小さいほうに制限|1 ソケットまたは 4 コアのいずれか小さいほうに制限| 
|1 つのインスタンスで使用される最大計算容量 - [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] または [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]|オペレーティング システムの最大容量|4 ソケットまたは 24 コアのいずれか小さいほうに制限|4 ソケットまたは 16 コアのいずれか小さいほうに制限|1 ソケットまたは 4 コアのいずれか小さいほうに制限|1 ソケットまたは 4 コアのいずれか小さいほうに制限|  
|[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] のインスタンスごとのバッファー プールの最大メモリ|オペレーティング システムの最大容量|128 GB|64 GB|1410 MB|1410 MB|
|[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] のインスタンスごとの列ストア セグメント キャッシュの最大メモリ|メモリ制限なし| 32 GB| 16 GB| 352 MB| 352 MB|  
|[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] のデータベースごとの最大メモリ最適化データ サイズ|メモリ制限なし| 32 GB| 16 GB| 352 MB| 352 MB|  
|利用可能な最大メモリ サイズ ( [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]のインスタンスごと)|オペレーティング システムの最大容量|テーブル: 16 GB<br /><br /> MOLAP: 64 GB|なし|なし|なし|  
|利用可能な最大メモリ サイズ ( [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]のインスタンスごと)|オペレーティング システムの最大容量|64 GB|64 GB|4 GB|なし|
|リレーショナル データベースの最大サイズ|524 PB|524 PB|524 PB|10 GB|10 GB|  
  
<sup>1</sup> Enterprise Edition with Server + Client Access License (CAL) に基づくライセンス (新しい使用許諾契約では利用できません) は、SQL Server インスタンスあたり最大 20 コアに制限されています。 コアベースのサーバー ライセンス モデルでは、制限はありません。 詳細については、「 [Compute Capacity Limits by Edition of SQL Server](../sql-server/compute-capacity-limits-by-edition-of-sql-server.md)」を参照してください。  
 
##  <a name="RDBMSHA"></a> RDBMS の高可用性  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Server Core サポート <sup>1</sup>|可|可|可|可|可|  
|ログ配布|可|可|可|いいえ|不可|  
|データベース ミラーリング|可|可<br /><br /> FULL SAFETY のみ|ミラーリング監視のみ|ミラーリング監視のみ|ミラーリング監視のみ| 
|バックアップ圧縮|可|可|いいえ|いいえ|不可| 
|データベース スナップショット|はい|可|可|可|はい|
|Always On フェールオーバー クラスター インスタンス|はい<br /><br /> ノードの数はオペレーティング システムの最大容量|はい<br /><br /> 2 つのノードのサポート|不可|いいえ|不可|  
|Always On 可用性グループ|可<br /><br /> 2 個の同期セカンダリ レプリカを含む最大 8 個のセカンダリ レプリカ|不可|いいえ|いいえ|不可|
|基本的な可用性グループ <sup>2</sup>|不可|可<br /><br /> 2 つのノードのサポート|不可|いいえ|不可|
|オンライン ページおよびファイルの復元|可|いいえ|いいえ|いいえ|不可|
|オンラインのインデックス構築|可|いいえ|いいえ|いいえ|不可|
|再開可能なオンライン インデックス リビルド|はい|いいえ|いいえ|いいえ|不可|
|オンラインのスキーマ変更|可|いいえ|いいえ|いいえ|不可|
|高速復旧|可|いいえ|いいえ|いいえ|不可|
|ミラー化バックアップ|可|いいえ|いいえ|いいえ|不可|
|ホット アド メモリと CPU|可|いいえ|いいえ|いいえ|不可|
|データベース復旧アドバイザー|可|可|可|可|可|
|暗号化されたバックアップ|可|可|いいえ|いいえ|不可|
|Windows Azure へのハイブリッド バックアップ (URL へのバックアップ)|可|可|いいえ|いいえ|不可|
|クラスターを使用しない可用性グループ|はい|可|可|いいえ|いいえ|不可|
|最小レプリカ コミット可用性グループ|はい|可|可|いいえ|いいえ|不可|
  
 <sup>1</sup> Server Core での SQL Server のインストールの詳細については、次を参照してください。 [Server Core 上の SQL Server のインストール](../database-engine/install-windows/install-sql-server-on-server-core.md)です。 

<sup>2</sup> 基本的な可用性グループの詳細については、「 [基本的な可用性グループ](../database-engine/availability-groups/windows/basic-availability-groups-always-on-availability-groups.md)」を参照してください。  

##  <a name="RDBMSSP"></a> RDBMS のスケーラビリティとパフォーマンス  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------| 
|列ストア <sup>1</sup>|はい|可|可|可|はい|  
|クラスター化列ストア インデックス内のラージ オブジェクト バイナリ|はい|可|可|可|はい|  
|オンライン非クラスター化列ストア インデックスのリビルド|はい|いいえ|いいえ|いいえ|不可|
|インメモリ OLTP <sup>1</sup>|はい|可|はい|はい <sup>2</sup>|はい|
|Stretch Database|可|可|可|可|可|
|恒久的なメイン メモリ|可|可|可|可|可|
|複数インスタンスのサポート|50|50|50|50|50|
|テーブルとインデックスのパーティション分割|はい|可|可|可|はい|  
|データ圧縮|はい|可|可|可|はい|
|リソース ガバナー|可|いいえ|いいえ|いいえ|不可|  
|パーティション テーブルの並列処理|可|いいえ|いいえ|いいえ|不可|
|複数の Filestream コンテナー|はい|可|可|可|はい|
|NUMA 対応のラージ ページ メモリとバッファー配列の割り当て|可|いいえ|いいえ|いいえ|不可|
|バッファー プール拡張|可|可|いいえ|いいえ|不可|
|IO リソース管理|可|いいえ|いいえ|いいえ|不可|  
|遅延持続性|可|可|可|可|はい|
|自動調整|はい|いいえ|いいえ|いいえ|不可|
|バッチ モード アダプティブ結合|はい|いいえ|いいえ|いいえ|不可|
|バッチ メモリ許可フィードバック|はい|いいえ|いいえ|いいえ|不可|
|一括挿入の機能強化|はい|可|可|可|可|


<sup>1</sup> インメモリ OLTP データ サイズおよび列ストア セグメント キャッシュは、「スケールの制限」セクションでエディションごとに指定されているメモリ量に制限されます。 並列処理には最大限度があります。 インデックス構築のための並列処理の度合い (DOP) は、Standard Edition では 2 DOP に、Web および Express Edition では 1 DOP に制限されます。 これは、ディスク ベース テーブルとメモリ最適化テーブルで作成された列ストア インデックスに当てはまります。

<sup>2</sup> LocalDB のインストール オプションには、この機能は含まれていません。

##  <a name="RDBMSS"></a> RDBMS のセキュリティ  
  
|機能|Enterprise|Standard|Web|Express|Express with Advanced Services|  
|-------------|----------------|--------------|---------|-------------|------------------------------------| 
|行レベルのセキュリティ|はい|可|可|可|はい|  
|Always Encrypted|はい|可|可|可|はい| 
|動的なデータ マスキング|可|可|可|可|はい|   
|基本的な監査|可|可|可|可|可| 
|詳細な監査|はい|可|可|可|はい| 
|透過的なデータベースの暗号化|可|いいえ|いいえ|いいえ|不可|   
|拡張キー管理|可|いいえ|いいえ|いいえ|不可| 
|ユーザー定義ロール|可|可|可|可|可| 
|包含データベース|可|可|可|可|可| 
|バックアップの暗号化|可|可|いいえ|いいえ|不可|  

##  <a name="Replication"></a> レプリケーション  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express|   
|-------------|----------------|--------------|---------|------------------------------------|------------------------| 
|異種サブスクライバー|可|可|いいえ|いいえ|不可|  
|マージ レプリケーション|可|可|可 (サブスクライバーのみ)|可 (サブスクライバーのみ)|可 (サブスクライバーのみ)|   
|Oracle パブリッシュ|可|いいえ|いいえ|いいえ|不可| 
|ピア ツー ピア トランザクション レプリケーション|可|いいえ|いいえ|いいえ|不可|   
|スナップショット レプリケーション|可|可|可 (サブスクライバーのみ)|可 (サブスクライバーのみ)|可 (サブスクライバーのみ)|   
|SQL Server の変更の追跡|可|可|可|可|可| 
|トランザクション レプリケーション|可|可|可 (サブスクライバーのみ)|可 (サブスクライバーのみ)|可 (サブスクライバーのみ)|   
|Azure へのトランザクション レプリケーション|可|可|いいえ|いいえ|不可|   
|トランザクション レプリケーションの更新可能サブスクリプション|可|いいえ|いいえ|いいえ|不可|  
  
##  <a name="SSMS"></a> 管理ツール  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express| 
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|SQL 管理オブジェクト (SMO)|可|可|可|可|可|  
|SQL 構成マネージャー|可|可|可|可|可|   
|SQL CMD (コマンド プロンプト ツール)|可|可|可|可|可|      
|分散再生 - 管理ツール|可|可|可|可|不可|  
|分散再生 - クライアント|可|可|可|いいえ|不可|  
|分散再生 - コントローラー|可 (最大 16 クライアント)|可 (1 クライアント)|可 (1 クライアント)|不可|不可|   
|SQL Profiler|可|可|不可 <sup>1</sup>|不可 <sup>1</sup>|不可 <sup>1</sup>|  
|SQL Server エージェント|可|可|可|いいえ|不可| 
|Microsoft System Center Operations Manager 管理パック|可|可|可|いいえ|不可|  
|データベース チューニング アドバイザー (DTA)|可|可 <sup>2</sup>|可 <sup>2</sup>|不可|不可|      
  
 <sup>1</sup> SQL Server Web、SQL Server Express、SQL Server Express with Tools、および SQL Server Express with Advanced Services は、SQL Server Standard および SQL Server Enterprise の各エディションを使用してプロファイルできます。  
  
 <sup>2</sup> チューニングは Standard Edition 機能でのみ有効です。  
  
##  <a name="RDBMSM"></a> RDBMS の管理の容易性  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express|   
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|ユーザー インスタンス|不可|いいえ|いいえ|はい|可| 
|LocalDB|不可|いいえ|いいえ|可|不可| 
|専用管理者接続|可|可|可|可 (トレース フラグを使用)|可 (トレース フラグを使用)|   
|PowerShell スクリプティングのサポート|可|可|可|可|可| 
|SysPrep のサポート <sup>1</sup>|可|可|可|可|可| 
|データ層アプリケーション コンポーネントの操作のサポート - 抽出、配置、アップグレード、削除|可|可|可|可|可| 
|ポリシー オートメーション (変更時とスケジュールに基づいて確認)|可|可|可|いいえ|不可|   
|パフォーマンス データ コレクター|可|可|可|いいえ|不可| 
|複数インスタンス管理でマネージ インスタンスとして登録できる|可|可|可|いいえ|不可|   
|標準的なパフォーマンス レポート|可|可|可|いいえ|不可| 
|プラン ガイドおよびプラン ガイドの固定計画|可|可|可|いいえ|不可|   
|NOEXPAND ヒントを使用したインデックス付きビューの直接クエリ|可|可|可|可|可| 
|インデックス付きビューの自動メンテナンス|可|可|可|いいえ|不可| 
|分散パーティション ビュー|可|いいえ|いいえ|いいえ|不可| 
|並列インデックス操作|可|いいえ|いいえ|いいえ|不可|  
|クエリ オプティマイザーによる自動的なインデックス付きのビュー使用|可|いいえ|いいえ|いいえ|不可| 
|並列整合性チェック|可|いいえ|いいえ|いいえ|不可| 
|SQL Server ユーティリティ コントロール ポイント|可|いいえ|いいえ|いいえ|不可|    
|バッファー プール拡張|可|可|いいえ|いいえ|不可| 
  
 <sup>1</sup> 詳細については、「 [SysPrep を使用した SQL Server のインストールに関する注意点](../database-engine/install-windows/considerations-for-installing-sql-server-using-sysprep.md)」を参照してください。  
 
##  <a name="DevTools"></a> 開発ツール  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express| 
|-------------|----------------|--------------|---------|------------------------------------|------------------------| 
|Microsoft Visual Studio の統合|可|可|可|可|可| 
|Intellisense (Transact-SQL および MDX)|可|可|可|可|可| 
|SQL Server Data Tools (SSDT)|可|可|可|可|不可|    
|MDX 編集、デバッグ、およびデザイン ツール|可|可|いいえ|いいえ|不可|   
  
##  <a name="Programmability"></a> Programmability  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express 
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|基本的な R 統合|可|可|可|可|不可|   
|高度な R 統合|可|いいえ|いいえ|いいえ|不可| 
|基本的な Python 統合|はい|可|可|可|不可|
|高度な Python 統合|はい|いいえ|いいえ|いいえ|不可| 
|Machine Learning Server (スタンドアロン)|はい|いいえ|いいえ|いいえ|不可|   
|Polybase コンピューティング ノード|可|可 <sup>1</sup>|可 <sup>1</sup>、 <sup>2</sup>|可 <sup>1</sup>、|可 <sup>1</sup>、 | 
|Polybase ヘッド ノード|可|いいえ|いいえ|いいえ|不可| 
|JSON|可|可|可|可|可|   
|クエリ ストア|可|可|可|可|可|   
|テンポラル|可|可|可|可|可|   
|共通言語ランタイム (CLR) 統合|可|可|可|可|可|   
|ネイティブ XML サポート|可|可|可|可|可| 
|XML インデックスの作成|可|可|可|可|可| 
|MERGE と UPSERT の機能|可|可|可|可|可|   
|FILESTREAM のサポート|可|可|可|可|可| 
|FileTable|可|可|可|可|可| 
|日付および時刻データ型|可|可|可|可|可|  
|国際化サポート|可|可|可|可|可| 
|フルテキストおよびセマンティック検索|可|可|可|可|不可| 
|クエリ内の言語指定|可|可|可|可|不可|   
|Service Broker (メッセージング)|可|可|不可 (クライアントのみ)|不可 (クライアントのみ)|不可 (クライアントのみ)|   
|Transact-SQL エンドポイント|可|可|可|いいえ|不可| 
|グラフ|はい|可|可|可|はい|  


<sup>1</sup> 複数のコンピューティング ノードでのスケール アウトにはヘッド ノードが必要です。

## <a name="IS"></a> Integration Services

[!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] の各エディションがサポートする Integration Services (SSIS) の機能については、「[Integration Services Features Supported by the Editions of SQL Server (SQL Server の各エディションがサポートする Integration Services の機能)](../integration-services/integration-services-features-supported-by-the-editions-of-sql-server.md)」をご覧ください。

##  <a name="MDS"></a> Master Data Services  
 については、[!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]と Data Quality Services 機能のエディションでサポートされる[!INCLUDE[ssNoVersion_md](../includes/ssNoVersion_md.md)]を参照してください[マスター データ サービスとデータ品質サービスでサポートされる機能のエディションの SQL Server](../master-data-services/master-data-services-and-data-quality-services-features-support.md)です。 

  
##  <a name="DW"></a> データ ウェアハウス  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express|   
|-------------|----------------|--------------|---------|------------------------------------|------------------------| 
|データベースを使用しないキューブ作成|可|可|いいえ|いいえ|不可 |   
|自動生成ステージングとデータ ウェアハウス スキーマ|可|可|いいえ|いいえ|不可| 
|変更データ キャプチャ|はい|可|いいえ|いいえ|不可| 
|スター結合クエリ最適化|可|いいえ|いいえ|いいえ|不可| 
|スケーラブルな読み取り専用の Analysis Services 構成|可|いいえ|いいえ|いいえ|不可| 
|パーティション テーブルとパーティション インデックスに対する並列クエリ処理|可|いいえ|いいえ|いいえ|不可|   
|グローバル バッチ集計|可|いいえ|いいえ|いいえ|不可| 

##  <a name="SSAS"></a> Analysis Services  
  
各エディションでサポートされている Analysis Services の機能について[!INCLUDE[ssNoVersion_md](../includes/ssNoVersion_md.md)]を参照してください[SQL Server のエディションでサポートされる Analysis Services 機能](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md)します。 
  
##  <a name="BIMD"></a> BI セマンティック モデル (多次元)  
  
各エディションでサポートされている Analysis Services の機能について[!INCLUDE[ssNoVersion_md](../includes/ssNoVersion_md.md)]を参照してください[SQL Server のエディションでサポートされる Analysis Services 機能](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md)します。
   
##  <a name="BIT"></a> BI セマンティック モデル (表形式)  
  
各エディションでサポートされている Analysis Services の機能について[!INCLUDE[ssNoVersion_md](../includes/ssNoVersion_md.md)]を参照してください[SQL Server のエディションでサポートされる Analysis Services 機能](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md)します。
  
##  <a name="PPSP"></a> Power Pivot for SharePoint  
  
Power Pivot for SharePoint の機能のエディションでサポートされるについて[!INCLUDE[ssNoVersion_md](../includes/ssNoVersion_md.md)]を参照してください[SQL Server のエディションでサポートされる Analysis Services 機能](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md)します。
  
##  <a name="DM"></a> データ マイニング  
  
各エディションでサポートされているデータ マイニング機能については[!INCLUDE[ssNoVersion_md](../includes/ssNoVersion_md.md)]を参照してください[SQL Server のエディションでサポートされる Analysis Services 機能](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md)します。
  
##  <a name="SSRS"></a> Reporting Services  
  
各エディションでサポートされている Reporting Services の機能について[!INCLUDE[ssNoVersion_md](../includes/ssNoVersion_md.md)]を参照してください[Reporting Services でサポートされる機能のエディションの SQL Server](../reporting-services/reporting-services-features-supported-by-the-editions-of-sql-server-2016.md)です。

##  <a name="BIC"></a> Business Intelligence クライアント  

各エディションでサポートされているビジネス インテリジェンス クライアント機能については[!INCLUDE[ssNoVersion_md](../includes/ssNoVersion_md.md)]を参照してください[SQL Server のエディションでサポートされる Analysis Services 機能](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md)または[Reporting Services でサポートされる機能のエディションの SQL Server](../reporting-services/reporting-services-features-supported-by-the-editions-of-sql-server-2016.md)です。
  
##  <a name="SLS"></a> 空間およびロケーション サービス  
  
|機能名|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|------------------|----------------|--------------|---------|------------------------------------|------------------------|
|空間インデックス|可|可|可|可|可|   
|平面データ型と測地データ型|可|可|可|可|可| 
|高度な空間的なライブラリ|可|可|可|可|可|   
|業界標準の空間データ形式のインポート/エクスポート|可|可|可|可|はい|   
  
##  <a name="ADS"></a> その他のデータベース サービス  
  
|機能名|Enterprise|Standard|Web|Express with Advanced Services|Express|   
|------------------|----------------|--------------|---------|------------------------------------|------------------------| 
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Migration Assistant|可|可|可|可|可|   
|データベース メール|可|可|可|いいえ|不可| 
  
##  <a name="Other"></a> その他のコンポーネント  
  
|機能名|Enterprise|Standard|Web|Express with Advanced Services|Express|   
|------------------|----------------|--------------|---------|------------------------------------|------------------------|  
|StreamInsight|StreamInsight Premium Edition|StreamInsight Standard Edition|StreamInsight Standard Edition|不可|不可| 
|StreamInsight HA|StreamInsight Premium Edition|不可|いいえ|いいえ|不可|   
  
> [![SSMS をダウンロードする](../analysis-services/media/download.png)](https://msdn.microsoft.com/library/mt238290.aspx) **[最新バージョンの SQL Server Management Studio をダウンロードする](https://msdn.microsoft.com/library/mt238290.aspx)**    
  
## <a name="next-steps"></a>次の手順 
 [SQL Server の製品仕様](http://msdn.microsoft.com/library/6445fd53-6844-4170-a86b-7fe76a9f64cb)   
 [SQL Server のインストール](../database-engine/install-windows/installation-for-sql-server-2016.md)  
 
  
  
