---
title: "テンポラル テーブルのシステム一貫性のチェック | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/07/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec081d42-57e4-43c7-9e1c-317ba8f23437
caps.latest.revision: 10
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: cb67454080657b99983e33e4c46858124b735433
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="temporal-table-system-consistency-checks"></a>テンポラル テーブルのシステム一貫性のチェック
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  テンポラル テーブルを使用する際、システムでは、スキーマがテンポラルの要件に準拠しているか、またそのデータに一貫性がありそれが維持されるかを確認する、さまざまな一貫性チェックが実行されます。 また、 **DBCC CHECKCONSTRAINTS** ステートメントにもテンポラル チェックが追加されています。  
  
## <a name="system-consistency-checks"></a>システムの一貫性のチェック  
 **SYSTEM_VERSIONING** を **ON**に設定する前に、履歴テーブルと現行テーブルに対し、一連のチェックが実行されます。 これらのチェックは、スキーマ チェックおよびデータ チェックにグループ化されます (履歴テーブルが空でない場合)。 また、システムではランタイムの一貫性チェックも実行されます。  
  
### <a name="schema-check"></a>スキーマのチェック  
 テーブルをテンポラル テーブルにするように作成または変更する場合、システムでは次の要件が満たされていることを確認します。  
  
1.  現行テーブルと履歴テーブルの双方の列名と列数が同じです。  
  
2.  現行テーブルと履歴テーブルのそれぞれの列のデータ型が一致しています。  
  
3.  期間列が **NOT NULL**に設定されています。  
  
4.  現行テーブルには主キーの制約がありますが、履歴テーブルには主キーの制約がありません。  
  
5.  履歴テーブルに、 **IDENTITY** 列が定義されていません。  
  
6.  履歴テーブルにトリガーが定義されていません。  
  
7.  履歴テーブルに外部キーが定義されていません。  
  
8.  履歴テーブルにテーブルまたは列の制約が定義されていません。 ただし、履歴テーブルで既定の列値は許可されています。  
  
9. 履歴テーブルが、読み取り専用のファイル グループに保存されていません。  
  
10. 履歴テーブルに、変更の追跡や変更データ キャプチャの構成がありません。  
  
### <a name="data-consistency-check"></a>データの一貫性チェック  
 **SYSTEM_VERSIONING** が **ON** に設定される前、任意の DML 操作の一環として、システムでは次のチェックを実行します。 **SysEndTime** ≥**SysStartTime**  
  
 既存の履歴テーブルへのリンクを作成する場合は、データの整合性チェックを実行することもできます。 このデータの一貫性チェックでは、既存のレコードに重複がなく、個々の各レコードでテンポラルの要件が満たされたことが確認されます。 データを実行する一貫性チェックが、既定値です。 一般に、データの一貫性は、履歴データが入力された既存の履歴テーブルを組み込む場合など、現行および履歴テーブルのデータ間に一貫性がない可能性がある場合に実行することをお勧めします。  
  
> [!WARNING]  
>  システム クロックを手動で変更すると、重複の状態 (つまり、レコードの終了時刻が開始時刻を上回っていること) を回避する実施されるランタイム データの一貫性チェックが失敗するため、システムで予期せず障害が発生します。  
  
## <a name="dbcc-checkconstraints"></a>DBCC CHECKCONSTRAINTS  
 **DBCC CHECKCONSTRAINTS** コマンドには、テンポラル データの一貫性チェックが含まれています。 詳細については、「[DBCC CHECKCONSTRAINTS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checkconstraints-transact-sql.md)」を参照してください。  
  
## <a name="did-this-article-help-you-were-listening"></a>この記事は役に立ちましたか? フィードバックをお待ちしております。  
 どのような情報をお探しでしたか? お探しの情報は見つかりましたか? コンテンツ改善のため、フィードバックをお待ちしています。 [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Temporal%20Table%20System%20Consistency%20Checks%20page) にコメントをお送りください  
  
## <a name="see-also"></a>参照  
 [テンポラル テーブル](../../relational-databases/tables/temporal-tables.md)   
 [システム バージョン管理されたテンポラル テーブルの概要](../../relational-databases/tables/getting-started-with-system-versioned-temporal-tables.md)   
 [テンポラル テーブルでのパーティション分割](../../relational-databases/tables/partitioning-with-temporal-tables.md)   
 [テンポラル テーブルの考慮事項と制約](../../relational-databases/tables/temporal-table-considerations-and-limitations.md)   
 [テンポラル テーブル セキュリティ](../../relational-databases/tables/temporal-table-security.md)   
 [システム バージョン管理されたテンポラル テーブルの履歴データの保有期間管理](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)   
 [メモリ最適化テーブルでのシステム バージョン管理されたテンポラル テーブル](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)   
 [テンポラル テーブル メタデータのビューおよび関数](../../relational-databases/tables/temporal-table-metadata-views-and-functions.md)  
  
  
