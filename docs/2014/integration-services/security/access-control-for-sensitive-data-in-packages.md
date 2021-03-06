---
title: パッケージ内の機微なデータへのアクセス制御 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- passwords [Integration Services]
- packages [Integration Services], security
- protection levels for packages [Integration Services]
- configuration files [Integration Services]
- encryption [Integration Services]
- cryptography [Integration Services]
- security [Integration Services], protection levels
ms.assetid: d4b073c4-4238-41fc-a258-4e114216e185
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 39c6316a6e256cf7dab161d57a032b777dfac09a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48163632"
---
# <a name="access-control-for-sensitive-data-in-packages"></a>パッケージ内の機微なデータへのアクセス制御
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージ内のデータを保護するために、保護レベルを設定できます。保護レベルを使用すると、パッケージ内の機微なデータのみを保護することも、すべてのデータを保護することもできます。 さらに、パスワードまたはユーザー キーでこのデータを暗号化したり、データベースを使用してデータを暗号化したりすることもできます。 また、パッケージに使用する保護レベルは静的である必要はなく、パッケージのライフ サイクルの各段階で変更できます。 多くの場合、開発中に保護レベルを 1 つ設定し、パッケージを配置した時点で別の保護レベルを設定します。  
  
> [!NOTE]  
>  このトピックで説明する保護レベルに加えて、固定データベース レベル ロールを使用して、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに保存されているパッケージを保護できます。  
  
## <a name="definition-of-sensitive-information"></a>機密情報の定義  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージでは、以下の情報が *機微*として定義されます。  
  
-   接続文字列のパスワード部。 すべてを暗号化するオプションを選択した場合は、接続文字列全体が機微であると見なされます。  
  
-   タスクによって生成され、「機微」とタグ付けされている XML ノード。 XML ノードのタグ付けは [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] によって制御されるので、ユーザーが変更することはできません。  
  
-   「機微」とマークされている任意の変数。 変数のマーク付けは、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]によって制御されます。  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] でプロパティが機微と見なされるかどうかは、接続マネージャーやタスクなど、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] コンポーネントの開発者がプロパティを機微として指定したかどうかによって決まります。 機微と見なされているプロパティの一覧では、ユーザーはプロパティを追加することも削除することもできません。  
  
## <a name="encryption"></a>暗号化  
 パッケージ保護レベルに採用されている暗号化処理は、マイクロソフトの暗号化 API (CryptoAPI) の一部である [!INCLUDE[msCoName](../../includes/msconame-md.md)] Data Protection API (DPAPI) を使用して実行されます。  
  
 パスワードを使用してパッケージを暗号化するパッケージ保護レベルでは、パスワードも指定する必要があります。 パスワードを使用しないレベルから使用するレベルに保護レベルを変更すると、パスワードを指定するよう要求されます。  
  
 また、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] では、パスワードを使用する保護レベルに対しては、 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] クラス ライブラリ (FCL) で提供される、キーの長さが 192 ビットの Triple DES 暗号アルゴリズムを使用しています。  
  
## <a name="protection-levels"></a>保護レベル  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] で提供される保護レベルを次の表に示します。 かっこで囲まれた値は、 <xref:Microsoft.SqlServer.Dts.Runtime.DTSProtectionLevel> 列挙の値です。 これらの値は、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でパッケージを操作するときにパッケージのプロパティを構成するために使用する [プロパティ] ウィンドウに表示されます。  
  
|保護レベル|説明|  
|----------------------|-----------------|  
|[機微なデータを保存しない] (`DontSaveSensitive`)|パッケージの保存時、パッケージ内の機微なプロパティの値は出力されません。 この保護レベルでは暗号化は行われません。その代わり、「機微」とマークされたプロパティは、パッケージと一緒に保存されません。その結果、他のユーザーが機微なデータを利用することはできません。 異なるユーザーがパッケージを開いた場合は、機微な情報が空白と置き換えられます。したがって、ユーザーは、機微な情報を指定する必要があります。<br /><br /> **dtutil** ユーティリティ (dtutil.exe) で使用する場合、この保護レベルに対応する値は 0 です。|  
|パスワードを使用してすべて暗号化 (`EncryptAllWithPassword`)|パスワードを使用してパッケージ全体を暗号化します。 暗号化処理には、パッケージを作成またはエクスポートしたときにユーザーによって指定されたパスワードが使用されます。 パッケージを [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで開くか、 **dtexec** コマンド プロンプト ユーティリティを使用して実行するには、パッケージ パスワードを指定する必要があります。 パスワードを指定しないと、パッケージにアクセスしたりパッケージを実行したりできません。<br /><br /> **dtutil** ユーティリティで使用する場合、この保護レベルに対応する値は 3 です。|  
|すべてのユーザー キーで暗号化 (`EncryptAllWithUserKey`)|現在のユーザー プロファイルに基づいたキーを使用してパッケージ全体を暗号化します。 パッケージを [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで開くか、 **dtexec** コマンド プロンプト ユーティリティを使用して実行できるのは、パッケージを作成またはエクスポートしたユーザーだけです。<br /><br /> **dtutil** ユーティリティで使用する場合、この保護レベルに対応する値は 4 です。<br /><br /> 注: ユーザー キーを使用する保護レベルに対しては、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] では DPAPI 標準を使用しています。 DPAPI の詳細については、[http://msdn.microsoft.com/library](http://go.microsoft.com/fwlink/?LinkId=15408) で MSDN ライブラリを参照してください。|  
|[機微なデータをパスワードで暗号化する] (`EncryptSensitiveWithPassword`)|パスワードを使用して、パッケージ内の機微なプロパティの値だけを暗号化します。 暗号化処理には、DPAPI が使用されます。 機微なデータはパッケージの一部として保存されます。ただし、このデータは、パッケージを作成またはエクスポートしたときに現在のユーザーによって指定されたパスワードを使用して暗号化されます。 パッケージを [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで開くには、ユーザーはパッケージ パスワードを指定する必要があります。 ユーザーがパスワードを指定しなかった場合、パッケージは機微なデータが取り除かれて開かれます。したがって、現在のユーザーは、機微なデータの新しい値を指定する必要があります。 パスワードを指定しないでパッケージを実行しようとした場合、パッケージの実行は失敗します。 パスワードとコマンド ラインの実行の詳細については、「 [dtexec Utility](../packages/dtexec-utility.md)」を参照してください。<br /><br /> **dtutil** ユーティリティで使用する場合、この保護レベルに対応する値は 2 です。|  
|[機微なデータをユーザー キーで暗号化する] (`EncryptSensitiveWithUserKey`)|現在のユーザー プロファイルに基づいたキーを使用して、パッケージ内の機微なプロパティの値だけを暗号化します。 同じプロファイルを使用している同じユーザーだけがパッケージを読み込むことができます。 異なるユーザーがパッケージを開いた場合は、機微な情報が空白と置き換えられます。したがって、現在のユーザーは、機微なデータの新しい値を指定する必要があります。 ユーザーがパッケージを実行しようとした場合、パッケージの実行は失敗します。 暗号化処理には、DPAPI が使用されます。<br /><br /> **dtutil** ユーティリティで使用する場合、この保護レベルに対応する値は 1 です。<br /><br /> 注: ユーザー キーを使用する保護レベルに対しては、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] では DPAPI 標準を使用しています。 DPAPI の詳細については、[http://msdn.microsoft.com/library](http://go.microsoft.com/fwlink/?LinkId=15408) で MSDN ライブラリを参照してください。|  
|暗号化をサーバー ストレージに依存 (`ServerStorage`)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース ロールを使用して、パッケージ全体を保護します。 このオプションは、パッケージを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb データベースに保存する場合にサポートされます。 さらに、SSISDB カタログを使用して、`ServerStorage`保護レベル<br /><br /> このオプションは、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]からパッケージをファイル システムに保存するときはサポートされません。|  
  
## <a name="protection-level-setting-and-the-ssisdb-catalog"></a>保護レベルの設定と SSISDB カタログ  
 SSISDB カタログを使用して、`ServerStorage`保護レベル。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに配置する場合、カタログは自動的にパッケージのデータと機微な値を暗号化します。 また、ユーザーがデータを取得するときには、自動的に暗号化を解除します。  
  
 プロジェクト (.ispac ファイル) をエクスポートするかどうか、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]サーバー ファイル システムをシステムは自動的に保護レベルを変更`EncryptSensitiveWithUserKey`します。 使用して、プロジェクトをインポートする場合、 **Integration Services インポート プロジェクト ウィザード**で[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]、 **ProtectionLevel**プロパティ、**プロパティ**ウィンドウ値を示した`EncryptSensitiveWithUserKey`します。  
  
## <a name="protection-level-setting-based-on-package-life-cycle"></a>パッケージのライフ サイクルに基づく保護レベルの設定  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] で初めて [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを開発するときは、パッケージの保護レベルを設定します。 パッケージの保護レベルは、後でパッケージを配置するとき、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]からインポートまたはエクスポートするとき、または [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] から [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージ ストア、またはファイル システムにコピーするときに、更新できます。 たとえば、作成したパッケージをユーザー キー保護レベル オプションの 1 つを指定してコンピューターに保存している場合、通常はそのパッケージを他のユーザーに渡すときに保護レベルを変更します。そのままでは、相手ユーザーがパッケージを開くことができません。  
  
 通常、次に示す手順に従って保護レベルを変更します。  
  
1.  開発中は、既定値に設定するパッケージの保護レベルのままに`EncryptSensitiveWithUserKey`します。 この設定により、開発者のみがパッケージの機密情報を参照できるようになります。 また、`EncryptAllWithUserKey` または `DontSaveSensitive` を使用することもできます。  
  
2.  パッケージを配置する時点で、開発者のユーザー キーに依存しない保護レベルに変更する必要があります。 したがって、通常は、`EncryptSensitiveWithPassword` または `EncryptAllWithPassword` を選択する必要があります。 運用環境の運用チームも知っている一時的な複雑なパスワードを割り当てて、パッケージを暗号化します。  
  
3.  パッケージが運用環境に配置されたら、運用チームは、チーム メンバーだけが知っている複雑なパスワードを割り当てて、配置されたパッケージを再度暗号化できます。 また、`EncryptSensitiveWithUserKey` または `EncryptAllWithUserKey` を選択し、パッケージを実行するアカウントのローカルの資格情報を使用して、配置されたパッケージを暗号化することもできます。  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [パッケージの保護レベルを設定または変更する](../set-or-change-the-protection-level-of-packages.md)  
  
## <a name="see-also"></a>参照  
 [パッケージ インポートおよびエクスポート&#40;SSIS サービス&#41;](../import-and-export-packages-ssis-service.md)   
 [Integration Services &#40;SSIS&#41;パッケージ](../integration-services-ssis-packages.md)   
 [セキュリティの概要&#40;Integration Services&#41;](security-overview-integration-services.md)  
  
  
