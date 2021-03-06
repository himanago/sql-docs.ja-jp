---
title: 統合認証を使用して |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- integrated authentication
ms.assetid: 9499ffdf-e0ee-4d3c-8bca-605371eb52d9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 24fce778851f514d680a2701cc9c4dcc9ccb277c
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2018
ms.locfileid: "52419073"
---
# <a name="using-integrated-authentication"></a>統合認証を使用する
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Linux および macOS での [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は、Kerberos 統合認証を使用する接続をサポートしています。 MIT Kerberos キー配布センター (KDC) をサポートしており、Generic Security Services Application Program Interface (GSSAPI) および Kerberos v5 ライブラリと連動します。
  
## <a name="using-integrated-authentication-to-connect-to-includessnoversionincludesssnoversion-mdmd-from-an-odbc-application"></a>統合認証を使用して ODBC アプリケーションから [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に接続する  

**SQLDriverConnect** または **SQLConnect** の接続文字列で **Trusted_Connection=yes** 指定して、Kerberos 統合認証を有効にすることができます。 例 :  

```
Driver='ODBC Driver 13 for SQL Server';Server=your_server;Trusted_Connection=yes  
```
  
DSN、接続するときに追加することも**Trusted_Connection = yes**の DSN エントリに`odbc.ini`します。
  
`-E`オプションの`sqlcmd`と`-T`オプションの`bcp`統合認証を指定することも使用できますはを参照してください[との接続**sqlcmd** ](../../../connect/odbc/linux-mac/connecting-with-sqlcmd.md)と。[使用した接続**bcp** ](../../../connect/odbc/linux-mac/connecting-with-bcp.md)詳細についてはします。

[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に接続するクライアント プリンシパルが、Kerberos KDC で既に認証されていることを確認します。
  
**ServerSPN** と **FailoverPartnerSPN** はサポートされていません。  
  
## <a name="deploying-a-linux-or-macos-odbc-driver-application-designed-to-run-as-a-service"></a>サービスとして実行するように、Linux または macOS の ODBC ドライバー アプリケーションを設計を展開します。

システム管理者は、サービスとして実行するアプリケーションを展開して、Kerberos 認証を使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に接続することができます。  
  
まず、クライアントで Kerberos を構成し、アプリケーションが既定のプリンシパルの Kerberos 資格情報を使用できることを確認する必要があります。

`kinit` または PAM (Pluggable Authentication Module) を使用し、次のいずれかの方法で、接続で使用されるプリンシパルの TGT を取得してキャッシュできるようにします。  
  
-   `kinit` を実行して、プリンシパル名とパスワードを渡します。  
  
-   `kinit` を実行して、プリンシパル名と、`ktutil` によって作成されたプリンシパルのキーを含む keytab ファイルの場所を渡します。  
  
-   Kerberos PAM (Pluggable Authentication Module) を使用してシステムにログインされたことを確認します。

アプリケーションがサービスとして実行されると、Kerberos の資格情報は有効期限が切れるように設計されているため、資格情報を更新して継続的なサービスの可用性を確保します。 ODBC ドライバーは更新されません。 資格情報自体です。あることを確認、`cron`ジョブまたは有効期限前に資格情報を更新する定期的に実行されるスクリプト。 更新のたびに、パスワードを必要とするを回避するには、keytab ファイルを使用することができます。  
  
[Kerberos の構成と使用](https://commons.oreilly.com/wiki/index.php/Linux_in_a_Windows_World/Centralized_Authentication_Tools/Kerberos_Configuration_and_Use) では、Linux 上でサービスを Kerberos 認証する方法の詳細を提供しています。
  
## <a name="tracking-access-to-a-database"></a>データベースへのアクセスを追跡する

データベース管理者は、システム アカウントを使用して統合認証を使用する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] にアクセスするときに、データベースへのアクセスの監査証跡を作成できます。  
  
[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] へのログインは、システム アカウントを使用し、Linux にはセキュリティ コンテキストを偽装する機能はありません。 そのため、ユーザーを特定するための詳細が必要です。
  
システム アカウント以外のユーザーに代わって [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 内のアクティビティを監査するには、アプリケーションで [!INCLUDE[tsql](../../../includes/tsql-md.md)] **EXECUTE AS** を使用する必要があります。  
  
アプリケーションのパフォーマンスを向上させるため、アプリケーションで接続プールを統合認証と監査とともに使用できます。 ただし、接続プール、統合認証、監査を組み合わせると、unixODBC ドライバー マネージャーがさまざまなユーザーにプールされた接続の再利用を許可するため、セキュリティ上のリスクが発生します。 詳細については、「 [ODBC Connection Pooling (ODBC 接続プール)](https://www.unixodbc.org/doc/conn_pool.html)」を参照してください。  

再利用する前に、アプリケーションは `sp_reset_connection` を実行してプールされた接続をリセットする必要があります。  

## <a name="using-active-directory-to-manage-user-identities"></a>Active Directory を使用して、ユーザー ID を管理する

アプリケーション システム管理者は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のログイン資格情報の個別セットを管理する必要はありません。 統合認証のキー配布センター (KDC) として Active Directory を構成することができます。 参照してください[Microsoft Kerberos](/windows/desktop/SecAuthN/microsoft-kerberos)詳細についてはします。

## <a name="using-linked-server-and-distributed-queries"></a>リンク サーバーと分散クエリを使用する

開発者は、SQL 資格情報の個別セットを保持するデータベース管理者がいなくても、リンク サーバーまたは分散クエリを使用するアプリケーションを展開できます。 この場合、開発者は統合認証を使用するアプリケーションを構成する必要があります。  
  
-   ユーザーは、クライアント コンピューターにログインし、アプリケーション サーバーに対して認証します。  
  
-   アプリケーション サーバーは異なるデータベースとして認証し、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に接続します。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は別のデータベース ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]) のデータベース ユーザーとして認証します。  
  
統合認証を構成すると、資格情報がリンク サーバーに渡されます。  
  
## <a name="integrated-authentication-and-sqlcmd"></a>統合認証 と sqlcmd
統合認証を使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] にアクセスするには、`sqlcmd` の `-E` オプションを使用します。 アカウントを実行することを確認`sqlcmd`は既定の Kerberos クライアント プリンシパルに関連付けられています。

## <a name="integrated-authentication-and-bcp"></a>統合認証 と bcp
統合認証を使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] にアクセスするには、`bcp` の `-T` オプションを使用します。 アカウントを実行することを確認`bcp`は既定の Kerberos クライアント プリンシパルに関連付けられています。 
  
使用するとエラーが`-T`で、`-U`または`-P`オプション。
  
## <a name="supported-syntax-for-an-spn-registered-by-includessnoversionincludesssnoversion-mdmd"></a>[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] によって登録された SPN でサポートされる構文

接続文字列または接続属性で SPN に使用される構文は次のとおりです。  

|構文|[説明]|  
|----------|---------------|  
|MSSQLSvc/*fqdn*:*port*|TCP が使用される場合にプロバイダーが生成する既定の SPN。 *port* は、TCP ポート番号です。 *fqdn* は完全修飾ドメイン名です。|  
  
## <a name="authenticating-a-linux-or-macos-computer-with-active-directory"></a>Active Directory を使用して Linux または macOS コンピューターを認証する

で Kerberos を構成するには、データを入力、`krb5.conf`ファイル。 `krb5.conf` `/etc/`などの構文を使用して別のファイルを参照することができますが、`export KRB5_CONFIG=/home/dbapp/etc/krb5.conf`します。 `krb5.conf` ファイルの例を以下に示します。  
  
```  
[libdefaults]  
default_realm = YYYY.CORP.CONTOSO.COM  
dns_lookup_realm = false  
dns_lookup_kdc = true  
ticket_lifetime = 24h  
forwardable = yes  
  
[domain_realm]  
.yyyy.corp.contoso.com = YYYY.CORP.CONTOSO.COM  
.zzzz.corp.contoso.com = ZZZZ.CORP.CONTOSO.COM  
```  
  
使用することができる場合、Linux または macOS コンピューターの構成を使用する DNS サーバーを提供する Windows DHCP サーバーで動的ホスト構成プロトコル (DHCP) を使用する、 **dns_lookup_kdc = true**します。 Kerberos を使用してコマンドを発行して、ドメインにサインインするようになりましたが、`kinit alias@YYYY.CORP.CONTOSO.COM`します。 渡されるパラメーター`kinit`大文字小文字を区別、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 、ドメインに存在するように構成するコンピューターは、そのユーザーをいる必要があります`alias@YYYY.CORP.CONTOSO.COM`ログイン用に追加します。 これで、信頼関係接続を使用することができます (接続文字列の **Trusted_Connection=YES**、**bcp -T**、または **sqlcmd -E**)。  
  
Linux または macOS コンピューターの時刻と時刻の Kerberos キー配布センター (KDC) では、閉じるである必要があります。 たとえばネットワーク タイム プロトコル (NTP) を使用して、システム時刻が正しく設定されていることを確認します。  

Kerberos 認証が失敗すると、Linux または macOS 上の ODBC ドライバーで NTLM 認証が使用されません。  

Linux または macOS のコンピューターと Active Directory の認証の詳細については、次を参照してください[Active Directory と Linux クライアントを認証](https://technet.microsoft.com/magazine/2008.12.linux.aspx#id0060048)と[OS X と Active Directoryに統合するためのベストプラクティス。](https://training.apple.com/pdf/Best_Practices_for_Integrating_OS_X_with_Active_Directory.pdf). Kerberos を構成する方法の詳細については、次を参照してください。、 [MIT Kerberos ドキュメント](https://web.mit.edu/kerberos/krb5-1.12/doc/index.html)します。

## <a name="see-also"></a>参照  
[プログラミング ガイドライン](../../../connect/odbc/linux-mac/programming-guidelines.md)

[リリース ノート](../../../connect/odbc/linux-mac/release-notes.md)

[Azure Active Directory の使用](../../../connect/odbc/using-azure-active-directory.md)
