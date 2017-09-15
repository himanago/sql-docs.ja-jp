---
title: "Create 要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Create Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Create
- urn:schemas-microsoft-com:xml-analysis#Create
- microsoft.xml.analysis.create
helpviewer_keywords:
- Create command (XMLA)
ms.assetid: a623d362-a1ac-40e4-8816-65fac89cb391
caps.latest.revision: 18
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a5420a85c65a29a09da519207206d3406c4cd384
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-element-xmla"></a>Create 要素 (XMLA)
  によって使用される Analysis Services スクリプト言語 (ASSL) 要素が含まれています、 **Execute**でオブジェクトを作成する方法、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Command>  
   <Create Scope="enum" AllowOverwrite="boolean">  
      <ParentObject>...</ParentObject>  
      <ObjectDefinition>...</ObjectDefinition>  
   </Create>  
</Command>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|子要素|[ObjectDefinition](../../../analysis-services/xmla/xml-elements-properties/objectdefinition-element-xmla.md)、 [ParentObject](../../../analysis-services/xmla/xml-elements-properties/parentobject-element-xmla.md)|  
  
## <a name="attributes"></a>属性  
  
|属性|Description|  
|---------------|-----------------|  
|AllowOverwrite|省略可能で、 **Boolean** 型の属性。 かどうかは True に設定すると、オブジェクトで定義されている、 **ObjectDefinition**要素は、上の既存のオブジェクトを上書きすることができます、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス。 この属性が省略されている場合、または False に設定されている場合は、オブジェクトが既に存在するとエラーが発生します。|  
|スコープ|省略可能な**Enum**属性。 定義されているオブジェクトの存続期間を定義、 **ObjectDefinition**要素。 この属性を省略するで定義されたオブジェクト、 **ObjectDefinition**要素が上に保持されます、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス。 次の値は、入手できます。<br /><br /> *セッション*: で定義されているオブジェクト、 **ObjectDefinition**要素は、XML for Analysis (XMLA) セッション中にのみ存在します。<br />                  使用すると、*セッション*を設定する、 **ObjectDefinition**要素を含めることができますのみ[ディメンション](../../../analysis-services/scripting/objects/dimension-element-assl.md)、[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)、または[MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md) ASSL の要素。|  
  
## <a name="remarks"></a>解説  
 各**作成**操作で指定された親の下の 1 つの主要なオブジェクトの作成、 **ParentObject**要素。 親オブジェクトが省略された場合、作成先の [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスと見なされます。 主要なオブジェクトの親が作成先のインスタンスでない場合には、これによってエラーが発生します。  
  
## <a name="example"></a>例  
 次の例は、という名前の空のデータベースを作成**テスト データベース**上、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス。  
  
```  
  
      <Create xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
   <ObjectDefinition>  
      <Database xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
         <Name>Test Database</Name>  
         <Description>A test database.</Description>  
      </Database>  
   </ObjectDefinition>  
</Create>  
```  
  
## <a name="see-also"></a>参照  
 [コマンドと #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  