---
title: "DQS ドメインに対してサポートされる SQL Server のデータ型と SSIS のデータ型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/08/2011"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4931143a-b84d-478b-9b45-174128d36ed3
caps.latest.revision: 7
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 7
---
# DQS ドメインに対してサポートされる SQL Server のデータ型と SSIS のデータ型
  SQL Server と SQL Server Integration Services (SSIS) にはさまざまなデータ型が存在しますが、DQS ドメインのデータ型は Date、Decimal、Integer、String の 4 つだけです。 SQL Server と SSIS のデータ型には、DQS でサポートされないものも存在します。 ソース データを DQS ドメインにマッピングし、データ品質アクティビティを実行できるのは、ソースのデータ型が DQS でサポートされていて、なおかつ DQS ドメインのデータ型と一致する場合だけです。 このトピックでは、SQL Server と SSIS のデータ型のうち、DQS ドメインの 4 つのデータ型にそれぞれマッピングできる、サポートされるデータ型について取り上げます。  
  
> [!NOTE]  
>  .xlsx および .xls ファイルでは、ソース列のデータ型は最初の 8 行で最も多く使用されているデータ型によって決定されます。 セルがそのデータ型に従っていない場合、セルの値は null になります。 同様に、.csv ファイルでは、ソース列のデータ型は最初の 8 行で最も多く使用されているデータ型によって決定されます。  
  
##  <a name="SQLServer"></a> サポートされる SQL Server のデータ型  
 次の表は、DQS ドメインの各データ型について、サポートされる SQL Server のデータ型を示しています。  
  
|DQS ドメインのデータ型|サポートされる SQL Server のデータ型|  
|--------------------------|------------------------------------|  
|日付|日付|  
|Decimal|Decimal<br /><br /> float<br /><br /> money<br /><br /> numeric<br /><br /> real<br /><br /> smallmoney|  
|Integer|bigint<br /><br /> int<br /><br /> smallint<br /><br /> tinyint|  
|文字列|char<br /><br /> nchar<br /><br /> nvarchar<br /><br /> varchar|  
  
 その他の SQL Server データ型は、DQS ではサポートされません。 SQL Server のすべてのデータ型については、次を参照してください。 [データの型と #40 です。Transact SQL と #41;](../t-sql/data-types/data-types-transact-sql.md)します。  
  
##  <a name="SSIS"></a> サポートされる SSIS のデータ型  
 次の表は、DQS ドメインの各データ型について、サポートされる SSIS のデータ型を示しています。  
  
|DQS ドメインのデータ型|サポートされる SSIS のデータ型|  
|--------------------------|------------------------------|  
|日付|DT_DATE|  
|Decimal|DT_DECIMAL<br /><br /> DT_NUMERIC<br /><br /> DT_R4<br /><br /> DT_R8|  
|Integer|DT_I1<br /><br /> DT_I2<br /><br /> DT_I4<br /><br /> DT_I8<br /><br /> DT_U1<br /><br /> DT_U2<br /><br /> DT_U4<br /><br /> DT_U8|  
|文字列|DT_STR<br /><br /> DT_WSTR|  
  
 その他の SSIS データ型は、DQS ではサポートされません。 SSIS のすべてのデータ型については、「 [Integration Services Data Types](../integration-services/data-flow/integration-services-data-types.md)」を参照してください。  
  
## 参照  
 [ドメインの管理](../data-quality-services/managing-a-domain.md)  
  
  