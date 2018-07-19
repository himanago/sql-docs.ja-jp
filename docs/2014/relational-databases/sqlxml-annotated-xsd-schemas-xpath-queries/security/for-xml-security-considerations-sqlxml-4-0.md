---
title: XML のセキュリティに関する考慮事項 (SQLXML 4.0) の |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- NESTED mode
- client-side XML formatting
- FOR XML clause, security
- server-side XML formatting
- AUTO mode
- security [SQLXML], FOR XML
ms.assetid: facba279-df93-475b-ad43-0043dc5bae03
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9fa6533dfa780c24dc46e578d5744317d50c356e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37258308"
---
# <a name="for-xml-security-considerations-sqlxml-40"></a>FOR XML のセキュリティに関する注意点 (SQLXML 4.0)
  FOR XML AUTO モードでは、XML 階層が生成され、要素名はテーブル名に、属性名は列名にマップされます。 この場合、データベースのテーブルと列の情報が公開されます。 AUTO モード (サーバー側の書式設定) を使用する場合は、テーブルと列の別名をクエリで指定することで、データベース情報を隠すことができます。 これらの別名は、結果の XML ドキュメント内に要素名および属性名として返されます。  
  
 たとえば、次のクエリでは AUTO モードを指定しており、XML の書式設定はサーバーで実行されます。  
  
```  
SELECT C.FirstName as F,C.LastName as L   
FROM Person.Contact C   
FOR XML AUTO  
```  
  
 結果の XML ドキュメントでは、要素名と属性名に別名が使用されます。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
  <C F="Nancy" L="Fuller" />   
  <CE F="Andrew" L="Peacock" />   
  <C F="Janet" L="Leverling" />   
  ...  
</root>  
```  
  
 NESTED モード (クライアント側の書式設定) を使用する場合、結果の XML ドキュメントでは、別名が属性にのみ返され、 ベース テーブルの名前が常に要素名として返されます。 たとえば、次のクエリでは NESTED モードを指定しています。  
  
```  
SELECT C.FirstName as F,C.LastName as L   
FROM Person.Contact C   
FOR XML AUTO  
```  
  
 結果の XML ドキュメントでは、ベース テーブルの名前が要素名として返され、テーブルの別名は使用されません。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
  <Person.Contact F="Nancy" L="Fuller" />   
  <Person.Contact F="Andrew" L="Peacock" />   
  <Person.Contact F="Janet" L="Leverling" />   
       ...  
</root>  
```  
  
  