---
title: sys.sp_cdc_generate_wrapper_function (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cdc_generate_wrapper_function_TSQL
- sp_cdc_generate_wrapper_function
- sys.sp_cdc_generate_wrapper_function_TSQL
- sys.sp_cdc_generate_wrapper_function
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_cdc_generate_wrapper_function
- sp_cdc_generate_wrapper_function
ms.assetid: 85bc086d-8a4e-4949-a23b-bf53044b925c
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 0ea44e7c2d9ca4f56d401688aa496aa851e563fe
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47780400"
---
# <a name="sysspcdcgeneratewrapperfunction-transact-sql"></a>sys.sp_cdc_generate_wrapper_function (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で使用可能な変更データ キャプチャのクエリ関数に必要なラッパー関数を作成するためのスクリプトを生成します。 生成されたラッパーでサポートされる API を使用すると、クエリ範囲を日時間隔として指定できます。 これによって関数は多くのウェアハウジング アプリケーション (変更データ キャプチャ テクノロジを使用して増分読み込みを確認している [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージ デザイナーが開発したアプリケーションなど) で使用しやすくなります。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.sp_cdc_generate_wrapper_function  
    [ [ @capture_instance sysname = ] 'capture_instance'  
    [ , [ @closed_high_end_point = ] closed_high_end_pt  
    [ , [ @column_list = ] 'column_list'  
```  
  
```  
  
[ , [ @update_flag_list = ] 'update_flag_list'  
```  
  
## <a name="arguments"></a>引数  
 [ @capture_instance=] '*capture_instance*'  
 スクリプトが生成されるキャプチャ インスタンスです。 *capture_instance*は**sysname**あり、既定値は NULL です。 値を省略するか、明示的に NULL に設定すると、すべてのキャプチャ インスタンスに対してラッパー スクリプトが作成されます。  
  
 [ @closed_high_end_point=] *high_end_pt_flag*  
 コミット時間が上端と等しい変更を、生成されたプロシージャによって抽出範囲内に含めるかどうかを示すフラグ ビットです。 *high_end_pt_flag*は**ビット**あり、既定値は 1 で、エンドポイントを含める必要があることを示します。 値に 0 を指定すると、すべてのコミット時間は上端よりも厳密に短くなります。  
  
 [ @column_list=] '*column_list*'  
 ラッパー関数から返される結果セットに含めるキャプチャ対象列の一覧です。 *column_list*は**nvarchar (max)** あり、既定値は NULL です。 NULL が指定されている場合、キャプチャされたすべての列が含まれます。  
  
 [ @update_flag_list=] '*update_flag_list*'  
 ラッパー関数から返される結果セットに更新フラグが含まれる付加列の一覧です。 *update_flag_list*は**nvarchar (max)** あり、既定値は NULL です。 NULL が指定されている場合、更新フラグは含まれません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|列の型|説明|  
|-----------------|-----------------|-----------------|  
|**function_name**|**nvarchar(145)**|生成された関数の名前です。|  
|**create_script**|**nvarchar(max)**|キャプチャ インスタンスのラッパー関数を作成するスクリプトです。|  
  
## <a name="remarks"></a>コメント  
 キャプチャ インスタンスのすべての変更クエリをラップする関数を作成するスクリプトが常に生成されます。 キャプチャ インスタンスが差分変更クエリをサポートする場合、このクエリのラッパーを生成するスクリプトも生成されます。  
  
## <a name="examples"></a>使用例  
 次の例では、`sys.sp_cdc_generate_wrapper_function` を使用して、すべての変更データ キャプチャ関数に対してラッパーを作成します。  
  
```  
DECLARE @wrapper_functions TABLE (  
    function_name sysname,  
    create_script nvarchar(max));  
  
INSERT INTO @wrapper_functions  
EXEC sys.sp_cdc_generate_wrapper_function;  
  
DECLARE @create_script nvarchar(max);  
DECLARE #hfunctions CURSOR LOCAL fast_forward  
FOR   
    SELECT create_script FROM @wrapper_functions;  
  
OPEN #hfunctions;  
FETCH #hfunctions INTO @create_script;  
WHILE (@@fetch_status <> -1)  
BEGIN  
    EXEC sp_executesql @create_script  
    FETCH #hfunctions INTO @create_script  
END;  
  
CLOSE #hfunctions;  
DEALLOCATE #hfunctions;  
```  
  
## <a name="see-also"></a>参照  
 [変更データ キャプチャ ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/change-data-capture-stored-procedures-transact-sql.md)   
 [変更データ キャプチャ&#40;SSIS&#41;](../../integration-services/change-data-capture/change-data-capture-ssis.md)  
  
  
