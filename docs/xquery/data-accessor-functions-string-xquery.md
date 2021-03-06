---
title: string 関数 (XQuery) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- string function
- fn:string function
ms.assetid: 7baa2959-9340-429b-ad53-3df03d8e13fc
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 4df87a9fedffa701858fef9101c58db12c1c3bf2
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51661681"
---
# <a name="data-accessor-functions---string-xquery"></a>データ アクセサー関数 - string (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  値を返します *$arg*を文字列として表されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
fn:string() as xs:string  
fn:string($arg as item()?) as xs:string  
```  
  
## <a name="arguments"></a>引数  
 *$arg*  
 ノードまたはアトミック値です。  
  
## <a name="remarks"></a>コメント  
  
-   場合 *$arg*空のシーケンスでは、長さ 0 の文字列が返されます。  
  
-   場合 *$arg*ノードで、関数は、文字列値のアクセサーを使用して取得したノードの文字列値を返します。 これは、W3C XQuery 1.0 and XPath 2.0 Data Model 仕様で定義されています。  
  
-   場合 *$arg*は、アトミック値としてキャスト式によって返されるのと同じ文字列を返します**xs:string**、 *$arg*、以外の場合、それ以外の場合に注意します。  
  
-   場合の種類 *$arg*は**xs:anyURI**URI は、特殊文字をエスケープせず、文字列に変換されます。  
  
-   この実装では、 **fn:string()** せず、引数は、コンテキストに依存する述語のコンテキストでのみ使用できます。 具体的には、角かっこ ([ ]) 内でしか使用できません。  
  
## <a name="examples"></a>使用例  
 このトピックではさまざまなに格納されている XML インスタンスに対して XQuery の例について**xml**型の列には、AdventureWorks データベース。  
  
### <a name="a-using-the-string-function"></a>A. string 関数の使用  
 次のクエリは、<`ProductDescription`> 要素の <`Features`> 子要素ノードを取得します。  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
 /PD:ProductDescription/PD:Features  
')  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 結果の一部を次に示します。  
  
```  
<PD:Features xmlns:PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">  
   These are the product highlights.   
   <p1:Warranty xmlns:p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    <p1:WarrantyPeriod>3 years</p1:WarrantyPeriod>  
    <p1:Description>parts and labor</p1:Description>  
   </p1:Warranty>  
       ...  
</PD:Features>  
```  
  
 指定した場合、 **string()** 関数の場合、指定したノードの文字列値を表示します。  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
 string(/PD:ProductDescription[1]/PD:Features[1])  
')  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 次に結果の一部を示します。  
  
```  
These are the product highlights.   
3 yearsparts and labor...    
```  
  
### <a name="b-using-the-string-function-on-various-nodes"></a>B. 異なるノードに対する string 関数の使用  
 次の例では、XML インスタンスが xml 型の変数に割り当てられています。 クエリが適用した結果を示すために指定された**string()** さまざまなノードにします。  
  
```  
declare @x xml  
set @x = '<?xml version="1.0" encoding="UTF-8" ?>  
<!--  This is a comment -->  
<root>  
  <a>10</a>  
just text  
  <b attr="x">20</b>  
</root>  
'  
```  
  
 次のクエリは、ドキュメント ノードの文字列値を取得します。 この値は、このノードの子孫にあたるすべてのテキスト ノードの文字列値を連結して生成されます。  
  
```  
select @x.query('string(/)')  
```  
  
 結果を次に示します。  
  
```  
This is a comment 10  
just text  
 20  
```  
  
 次のクエリは、processing-instruction ノードの文字列値を取得します。 ただし、このノードにはテキスト ノードが含まれていないため、空のシーケンスが結果として返されます。  
  
```  
select @x.query('string(/processing-instruction()[1])')  
```  
  
 次のクエリは、comment ノードの文字列値を取得し、そのテキスト ノードを返します。  
  
```  
select @x.query('string(/comment()[1])')  
```  
  
 結果を次に示します。  
  
```  
This is a comment   
```  
  
## <a name="see-also"></a>参照  
 [xml データ型に対する XQuery 関数](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
