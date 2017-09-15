---
title: "署名を追加する (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ADD SIGNATURE
- ADD_SIGNATURE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ADD SIGNATURE statement
- adding digital signatures
- signatures [SQL Server]
- digital signatures [SQL Server]
ms.assetid: 64d8b682-6ec1-4e5b-8aee-3ba11e72d21f
caps.latest.revision: 50
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d171b17749cbe5333a11405eb48ac4b9293151d6
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="add-signature-transact-sql"></a>ADD SIGNATURE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  ストアド プロシージャ、関数、アセンブリ、またはトリガーにデジタル署名を追加します。 また、ストアド プロシージャ、関数、アセンブリ、またはトリガーに副署名を追加します。  
  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
ADD [ COUNTER ] SIGNATURE TO module_class::module_name   
    BY <crypto_list> [ ,...n ]  
  
<crypto_list> ::=  
    CERTIFICATE cert_name  
    | CERTIFICATE cert_name [ WITH PASSWORD = 'password' ]  
    | CERTIFICATE cert_name WITH SIGNATURE = signed_blob   
    | ASYMMETRIC KEY Asym_Key_Name  
    | ASYMMETRIC KEY Asym_Key_Name [ WITH PASSWORD = 'password'.]  
    | ASYMMETRIC KEY Asym_Key_Name WITH SIGNATURE = signed_blob  
```  
  
## <a name="arguments"></a>引数  
 *module_class*  
 署名を追加するモジュールのクラスです。 スキーマ スコープのモジュールの既定値は OBJECT です。  
  
 *モジュール名*  
 署名または副署名の対象となるストアド プロシージャ、関数、アセンブリ、またはトリガーの名前を指定します。  
  
 証明書*cert_name*  
 ストアド プロシージャ、関数、アセンブリ、またはトリガーの署名または副署名に使用する証明書の名前を指定します。  
  
 パスワード ='*パスワード*'  
 証明書または非対称キーの秘密キーの暗号化解除に必要なパスワードです。 この句は、秘密キーがデータベースのマスター キーで保護されていない場合にのみ必要です。  
  
 署名 =*signed_blob*  
 モジュールの署名付きバイナリ ラージ オブジェクト (BLOB) を指定します。 この句を使用すると、秘密キーを配布せずにモジュールを配布する場合に便利です。 この句を使用する場合、署名付きバイナリ ラージ オブジェクトをデータベースに追加するときに必要となるのは、モジュール、署名、公開キーだけです。 *signed_blob*は 16 進数形式自体の blob。  
  
 非対称キー *Asym_Key_Name*  
 ストアド プロシージャ、関数、アセンブリ、またはトリガーの署名または副署名に使用する非対称キーの名前を指定します。  
  
## <a name="remarks"></a>解説  
 署名されているモジュールまたは副し、証明書または署名を使用する非対称キーは既に存在しています。 署名の確認で、モジュールのすべての文字が確認されます。 これには、先頭のキャリッジ リターンとライン フィードも含まれます。  
  
 モジュールの署名および証明書と非対称キーの任意の数で副できます。  
  
 モジュールが変更された場合、モジュールの署名は削除されます。  
  
 モジュールに EXECUTE AS 句が含まれる場合、署名の処理の一部としてプリンシパルのセキュリティ ID (SID) も含まれます。  
  
> [!CAUTION]  
>  モジュールの署名は権限の許可のみに使用し、権限の拒否または取り消しには使用しないでください。  
  
 インライン テーブル値関数には署名できません。  
  
 署名に関する情報は、sys.crypt_properties カタログ ビューで確認できます。  
  
> [!WARNING]  
>  署名のプロシージャを再作成する場合は、元のバッチ内のすべてのステートメントが再作成のバッチと一致する必要があります。 バッチの一部が異なる場合は、スペースやコメントの違いだけであっても、異なる署名になります。  
  
## <a name="countersignatures"></a>副署名  
 SQL トークンに署名を一時的に追加する署名付きモジュールを実行するときに、モジュールが別のモジュールを実行する場合、またはモジュールの実行が終了した場合、署名は失われます。 副署名は、署名の特殊な形式です。 副署名のみで権限が付与されることはありませんが、副署名されたオブジェクトに対して行われた呼び出しの間、同じ証明書または非対称キーで作成された署名を保持できるようになります。  
  
 たとえば、ユーザー Alice がプロシージャ ProcSelectT1ForAlice を呼び出すとします。このプロシージャを呼び出すと、テーブル T1 から選択を行うプロシージャ procSelectT1 が呼び出されます。 Alice は ProcSelectT1ForAlice および procSelectT1 に対する EXECUTE 権限を持っていますが、T1 に対する SELECT 権限は持っておらず、このチェーン全体に組み合わせ所有権は関係しません。 Alice は、テーブル T1 に直接アクセスすることも、ProcSelectT1ForAlice および procSelectT1 を使用してアクセスすることもできません。 Alice がアクセスを常に ProcSelectT1ForAlice を使用するので、procSelectT1 を実行する権限を付与したくありません。 このためにはどうすればよいでしょうか。  
  
-   procSelectT1 に署名して procSelectT1 が T1 にアクセスできるようにすると、Alice は procSelectT1 を直接呼び出すことができるようになり、ProcSelectT1ForAlice を呼び出す必要がありません。  
  
-   procSelectT1 に対する EXECUTE 権限を Alice に付与しないということもできますが、Alice は ProcSelectT1ForAlice を使用して procSelectT1 を呼び出すこともできなくなります。  
  
-   ProcSelectT1ForAlice への署名は procSelectT1 の呼び出し時に失われるので、この署名だけでは効果がありません。  
  
ただしで、ProcSelectT1ForAlice の署名に使用される同じ証明書で procSelectT1 に副署名[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]呼び出しチェーン全体で署名が保持して、T1 にアクセスが許可されます。 Alice が procSelectT1 を直接呼び出そうとしても、副署名では権限は付与されないので、T1 にはアクセスできません。 以下の例 C で、この例の [!INCLUDE[tsql](../../includes/tsql-md.md)] を示します。  
  
## <a name="permissions"></a>Permissions  
 オブジェクトに対する ALTER 権限と、証明書または非対称キーに対する CONTROL 権限が必要です。 関連付けられている秘密キーがパスワードで保護されている場合、ユーザーはそのパスワードも保持している必要があります。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-signing-a-stored-procedure-by-using-a-certificate"></a>A. 証明書を使用してストアド プロシージャに署名する  
 次の例では、ストアド プロシージャ `HumanResources.uspUpdateEmployeeLogin` に対して、証明書 `HumanResourcesDP` を使用して署名を行います。  
  
```  
USE AdventureWorks2012;  
ADD SIGNATURE TO HumanResources.uspUpdateEmployeeLogin   
    BY CERTIFICATE HumanResourcesDP;  
GO  
```  
  
### <a name="b-signing-a-stored-procedure-by-using-a-signed-blob"></a>B. 署名付き BLOB を使用してストアド プロシージャに署名する  
 次の例では、新しいデータベースを作成し、この例で使用する証明書を作成します。 この例は、作成および単純なストアド プロシージャに署名し、署名付き BLOB を取得から`sys.crypt_properties`です。 その後、署名は削除され、再度追加されます。 次の例では、WITH SIGNATURE 構文を使用して、このプロシージャに署名します。  
  
```  
CREATE DATABASE TestSignature ;  
GO  
USE TestSignature ;  
GO  
-- Create a CERTIFICATE to sign the procedure.  
CREATE CERTIFICATE cert_signature_demo   
    ENCRYPTION BY PASSWORD = 'pGFD4bb925DGvbd2439587y'  
    WITH SUBJECT = 'ADD SIGNATURE demo';  
GO  
-- Create a simple procedure.  
CREATE PROC [sp_signature_demo]  
AS  
    PRINT 'This is the content of the procedure.' ;  
GO  
-- Sign the procedure.  
ADD SIGNATURE TO [sp_signature_demo]   
    BY CERTIFICATE [cert_signature_demo]   
    WITH PASSWORD = 'pGFD4bb925DGvbd2439587y' ;  
GO  
-- Get the signature binary BLOB for the sp_signature_demo procedure.  
SELECT cp.crypt_property  
    FROM sys.crypt_properties AS cp  
    JOIN sys.certificates AS cer  
        ON cp.thumbprint = cer.thumbprint  
    WHERE cer.name = 'cert_signature_demo' ;  
GO  
```  
  
 `crypt_property`このステートメントによって返される署名を変更するプロシージャを作成します。 この結果は、この例の後半で使用するためにメモしておきます。 この例で示される結果は:`0x831F5530C86CC8ED606E5BC2720DA835351E46219A6D5DE9CE546297B88AEF3B6A7051891AF3EE7A68EAB37CD8380988B4C3F7469C8EABDD9579A2A5C507A4482905C2F24024FFB2F9BD7A953DD5E98470C4AA90CE83237739BB5FAE7BAC796E7710BDE291B03C43582F6F2D3B381F2102EEF8407731E01A51E24D808D54B373`です。  
  
```  
-- Drop the signature so that it can be signed again.  
DROP SIGNATURE FROM [sp_signature_demo]   
    BY CERTIFICATE [cert_signature_demo];  
GO  
-- Add the signature. Use the signature BLOB obtained earlier.  
ADD SIGNATURE TO [sp_signature_demo]   
    BY CERTIFICATE [cert_signature_demo]  
    WITH SIGNATURE = 0x831F5530C86CC8ED606E5BC2720DA835351E46219A6D5DE9CE546297B88AEF3B6A7051891AF3EE7A68EAB37CD8380988B4C3F7469C8EABDD9579A2A5C507A4482905C2F24024FFB2F9BD7A953DD5E98470C4AA90CE83237739BB5FAE7BAC796E7710BDE291B03C43582F6F2D3B381F2102EEF8407731E01A51E24D808D54B373 ;  
GO  
```  
  
### <a name="c-accessing-a-procedure-using-a-countersignature"></a>C. 副署名を使用してプロシージャにアクセスする  
 次の例では、副署名によってオブジェクトへのアクセスを制御する方法を示します。  
  
```  
-- Create tesT1 database  
CREATE DATABASE testDB;  
GO  
USE testDB;  
GO  
-- Create table T1  
CREATE TABLE T1 (c varchar(11));  
INSERT INTO T1 VALUES ('This is T1.');  
  
-- Create a TestUser user to own table T1  
CREATE USER TestUser WITHOUT LOGIN;  
ALTER AUTHORIZATION ON T1 TO TestUser;  
  
-- Create a certificate for signing  
CREATE CERTIFICATE csSelectT  
  ENCRYPTION BY PASSWORD = 'SimplePwd01'  
  WITH SUBJECT = 'Certificate used to grant SELECT on T1';  
CREATE USER ucsSelectT1 FROM CERTIFICATE csSelectT;  
GRANT SELECT ON T1 TO ucsSelectT1;  
  
-- Create a principal with low privileges  
CREATE LOGIN Alice WITH PASSWORD = 'SimplePwd01';  
CREATE USER Alice;  
  
-- Verify Alice cannoT1 access T1;  
EXECUTE AS LOGIN = 'Alice';  
    SELECT * FROM T1;  
REVERT;  
  
-- Create a procedure that directly accesses T1  
CREATE PROCEDURE procSelectT1 AS  
BEGIN  
    PRINT 'Now selecting from T1...';  
    SELECT * FROM T1;  
END;  
GO  
GRANT EXECUTE ON procSelectT1 to public;  
  
-- Create special procedure for accessing T1  
CREATE PROCEDURE  procSelectT1ForAlice AS  
BEGIN  
   IF USER_ID() <> USER_ID('Alice')  
    BEGIN  
        PRINT 'Only Alice can use this.';  
        RETURN  
    END  
   EXEC procSelectT1;  
END;  
GO;  
GRANT EXECUTE ON procSelectT1ForAlice TO PUBLIC;  
  
-- Verify procedure works for a sysadmin user  
EXEC procSelectT1ForAlice;  
  
-- Alice still can't use the procedure yet  
EXECUTE AS LOGIN = 'Alice';  
    EXEC procSelectT1ForAlice;  
REVERT;  
  
-- Sign procedure to grant it SELECT permission  
ADD SIGNATURE TO procSelectT1ForAlice BY CERTIFICATE csSelectT   
WITH PASSWORD = 'SimplePwd01';  
  
-- Counter sign proc_select_t, to make this work  
ADD COUNTER SIGNATURE TO procSelectT1 BY CERTIFICATE csSelectT   
WITH PASSWORD = 'SimplePwd01';  
  
-- Now the proc works.   
-- Note that calling procSelectT1 directly still doesn't work  
EXECUTE AS LOGIN = 'Alice';  
    EXEC procSelectT1ForAlice;  
    EXEC procSelectT1;  
REVERT;  
  
-- Cleanup  
USE master;  
GO  
DROP DATABASE testDB;  
DROP LOGIN Alice;  
  
```  
  
## <a name="see-also"></a>参照  
 [sys.crypt_properties & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-crypt-properties-transact-sql.md)   
 [DROP SIGNATURE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-signature-transact-sql.md)  
  
  
