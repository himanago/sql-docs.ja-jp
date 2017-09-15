---
title: "MDSCHEMA_INPUT_DATASOURCES 行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- MDSCHEMA_INPUT_DATASOURCES
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- MDSCHEMA_INPUT_DATASOURCES rowset
ms.assetid: 12482fd5-16e3-4171-9cb0-76d0d4f5308e
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e105cc8151640f5d5d74d6c7c76cc52edc16a242
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="mdschemainputdatasources-rowset"></a>MDSCHEMA_INPUT_DATASOURCES 行セット
  データベース内で定義されたデータ ソースについて記述します。  
  
## <a name="rowset-columns"></a>行セットの列  
 **MDSCHEMA_INPUT_DATASOURCES**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**||このデータ ソースが所属するカタログの名前。|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**||サポートされていません。|  
|**DATASOURCE_NAME**|**DBTYPE_WSTR**||データ ソース オブジェクトの名前。|  
|**DATASOURCE_TYPE**|**DBTYPE_WSTR**||データ ソースの種類。 有効な値は次のとおりです。<br /><br /> **リレーショナル**<br /><br /> **Olap**|  
|**CREATED_ON**|**DBTYPE_DBTIMESTAMP**||データ ソースの作成日。|  
|**LAST_SCHEMA_UPDATE**|**DBTYPE_DBTIMESTAMP**||データ ソースの最終変更日時。|  
|**DESCRIPTION**|**DBTYPE_WSTR**||アクションについてのわかりやすい説明。|  
|**タイムアウト**|**DBTYPE_UI4**||データ ソースのタイムアウト。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="restriction-columns"></a>制限の列  
 **MDSCHEMA_INPUT_DATASOURCES**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|省略可。|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|省略可。|  
|**DATASOURCE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**DATASOURCE_TYPE**|**DBTYPE_WSTR**|省略可。|  
  
## <a name="see-also"></a>参照  
 [OLE DB for OLAP スキーマ行セット](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  