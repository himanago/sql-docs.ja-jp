---
title: "updateNString (java.lang.String, java.lang.String) メソッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6daca03f-c60f-4842-b9e3-11d136e78312
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f332fb16c0deb06964158518debe81d68d08e287
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="updatenstring-method-javalangstring-javalangstring"></a>updateNString (java.lang.String, java.lang.String) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された列の更新、**文字列**値の指定した列のラベルを使用します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void updateNString(java.lang.String columnLabel,  
                          java.lang.String nString)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnLabel*  
  
 A**文字列**列ラベルを格納しています。  
  
 *nString*  
  
 A**文字列**オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この updateNString メソッドは、java.sql.ResultSet インターフェイスの updateNString メソッドによって指定されます。  
  
 このメソッドは Java**文字列**に選択した**nchar**、 **nvarchar (max)**、 **ntext**、および**xml**列です。 このメソッドを他のデータ型の列で使用すると、例外がスローされます。  
  
## <a name="see-also"></a>参照  
 [updateNString メソッド & #40 です。SQLServerResultSet &#41;](../../../connect/jdbc/reference/updatenstring-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  