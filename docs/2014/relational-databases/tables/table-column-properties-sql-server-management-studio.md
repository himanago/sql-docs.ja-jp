---
title: テーブル列のプロパティ (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:65558
- vdtsql.chm:69657
- vdt.ppg.columns
ms.assetid: 09830897-cc10-46b8-95f5-e0e9681b668c
caps.latest.revision: 31
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4c84cca055d927dc617fea1aebce6c6401eaa991
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37215162"
---
# <a name="table-column-properties-sql-server-management-studio"></a>テーブル列のプロパティ (SQL Server Management Studio)
  これらのプロパティは、テーブル デザイナーの下部ペインに表示されます。 特に断りのない限り、列が選択されているときにこれらのプロパティを [プロパティ] ウィンドウで編集できます。 **[列のプロパティ]** は、カテゴリ別またはアルファベット順に表示できます。 多くのプロパティは表示されるだけであり、変更できるのは特定のデータ型についてのみです。  
  
> [!NOTE]  
>  テーブルをレプリケーション用にパブリッシュする場合は、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) か [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理オブジェクト (SMO) を使用して、スキーマを変更する必要があります。 テーブル デザイナーまたはデータベース ダイアグラム デザイナーを使用してスキーマを変更するとき、テーブルはいったん削除されてから再作成されます。 パブリッシュされたオブジェクトは削除できないので、スキーマの変更は失敗します。  
  
 **全般**  
 展開すると、 **[オブジェクト名]**、 **[Null を許容]**、 **[データ型]**、 **[既定値またはバインド]**、 **[長さ]**、 **[有効桁数]**、 **[小数点以下桁数]** が表示されます。  
  
 **名前**  
 選択した列の名前を表示します。  
  
 **[Null を許容]**  
 この列で null が許容されるかどうかを示します。 このプロパティを編集するには、テーブル デザイナーの上部ペインの列に対応する [Null を許容] チェック ボックスをオンにします。  
  
 **[データ型]**  
 選択した列のデータ型を表示します。 このプロパティを編集するには、値をクリックしてドロップダウン リストを展開し、別の値を選択します。  
  
 **[既定値またはバインド]**  
 この列に値が指定されていないときの既定値を表示します。 このフィールドの値は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定の制約の値か、列がバインドされているグローバル制約の名前になります。 ドロップダウン リストには、データベースに定義されているすべてのグローバル既定値が含まれています。 列にグローバル既定値をバインドする場合は、ドロップダウン リストから選択します。 列に既定の制約を作成する場合は、既定値をテキストとして直接入力します。  
  
 **[長さ]**  
 文字ベースのデータ型で許容される文字数が表示されます。 このプロパティは、文字に基づくデータ型にのみ使用できます。  
  
 **[小数点以下桁数]**  
 この列の値に使用できる小数点以下の最大桁数を表示します。 数値データ型でないデータ型の場合、このプロパティには **0** と表示されます。  
  
 **[有効桁数]**  
 この列の値に使用できる最大桁数を表示します。 数値データ型でないデータ型の場合、このプロパティには **0** と表示されます。  
  
 **テーブル デザイナー (Table Designer)**  
 **[テーブル デザイナー]** セクションを拡張します。  
  
 **[照合順序]**  
 クエリ結果の行を並べ替えるために列値が使用されるときに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が既定で列に適用する照合順序を表示します。 照合順序を編集するには、プロパティを選択し、プロパティ値の右側にある省略記号 ([...]) をクリックして **[照合順序]** ダイアログ ボックスを表示します。  
  
 **[計算列の指定]**  
 計算列に関する情報を表示します。 このプロパティに表示される値は、 **[数式]** 子プロパティの値と同じであり、計算列の式が表示されます。  
  
> [!NOTE]  
>  **[計算列の指定]** プロパティに対して表示される値を変更するには、このプロパティを展開し、 **[数式]** 子プロパティを編集します。  
  
-   **[数式]** 計算列の式を表示します。 このプロパティを編集するには、新しい式を直接入力します。  
  
-   **[Is Persisted]** 式の結果を格納するかどうかが示されます。 このプロパティを **[いいえ]** に設定した場合は、式だけが格納され、値はこの列が参照されるごとに計算されます。 このプロパティを編集するには、値をクリックしてドロップダウン リストを展開し、別の値を選択します。  
  
 詳細については、「 [テーブルの計算列の指定](../tables/specify-computed-columns-in-a-table.md)」を参照してください。  
  
 **[圧縮データ型]**  
 フィールドのデータ型に関する情報が表示されます。SQL の CREATE TABLE ステートメントと同じ形式で表示されます。 たとえば、最大 20 文字の可変長文字列のフィールドは、"varchar(20)" と表示されます。 このプロパティを変更するには、値を直接入力します。  
  
 **説明**  
 この列を説明するテキストを表示します。 説明を編集するには、プロパティを選択し、プロパティ値の右側にある省略記号 ([...]) をクリックします。次に、 **[説明のプロパティ]** ダイアログ ボックスで説明を編集します。  
  
 **決定的**  
 選択した列のデータ型を明確に決定できるかどうかが表示されます   
  
 **[DTS パブリッシュ済み]**  
 列が SSIS によりパブリッシュされているかどうかが表示されます  
  
 **[フルテキストの指定]**  
 フルテキスト インデックスに関する情報を表示します。 このプロパティの値は、 **[フルテキスト インデックス化されている]** 子プロパティの値であり、この列にフルテキスト インデックスが付けられているかどうかを示します。  
  
> [!NOTE]  
>  **[フルテキストの指定]** プロパティに対して表示される値を変更するには、このプロパティを展開し、 **[フルテキスト インデックス化されている]** 子プロパティを編集します。  
  
-   **[フルテキスト インデックス化されている]** この列にフルテキスト インデックスが付けられているかどうかを示します。 この列のデータ型がフルテキスト検索に対応している場合、およびこの列が属するテーブルにフルテキスト インデックスが指定されている場合にのみ、このプロパティを **[はい]** に設定できます。 このプロパティを編集するには、値をクリックしてドロップダウン リストを展開し、値を選択します。  
  
-   **[フルテキスト型列]** この列のフルテキスト インデックスが設定されている列の名前を示します。 この列の **[データ型]** プロパティが **[image]** または **[varbinary]** の場合は、このプロパティを設定する必要があります。 このプロパティで指定される列は、 **[n]char、[n]varchar** 、または **xml**型である必要があります。このプロパティのドロップダウン リストには、これらの 3 種類のいずれかのデータ型を持つ列のみが表示されます。 このプロパティで指定された列の行は、フルテキスト検索ができる列の行と一致するドキュメントの種類を示します。 このプロパティを編集するには、値をクリックしてドロップダウン リストを展開し、別の値を選択します。  
  
-   **[言語]** 列にインデックスを付けるために使用するワード ブレーカーの言語を示します。 プロパティに格納される値は、実際はワード ブレーカーのロケール識別子です。 ワード ブレーカーおよび LCID の詳細については、「ワード ブレーカーとステミング機能」を参照してください。 このプロパティを編集するには、値をクリックしてドロップダウン リストを展開し、別の値を選択します。  
  
 **[統計的セマンティクス]**  
 選択されている列に対する統計的セマンティック インデックスを有効にするかどうかを選択します。 詳細については、「[セマンティック検索 &#40;SQL Server&#41;](../search/semantic-search-sql-server.md)」を参照してください。  
  
 **[統計的セマンティクス]** を選択する前に **[言語]** を選択した場合、選択した言語にセマンティック言語モデルが関連付けられていなければ、**[統計的セマンティクス]** オプションは **[いいえ]** に設定され、変更できません。 **[言語]** を選択する前に **[統計的セマンティクス]** オプションで **[はい]** を選択した場合、 **[言語]** 列で使用できる言語は、セマンティック言語モデルでサポートされているものだけに制限されます。  
  
 **[SQL Server 以外のサブスクライバーがある]**  
 列を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サブスクライバー以外のサブスクライバーにレプリケートするかどうかを示します。  
  
 **[IDENTITY の指定]**  
 列の値に対して一意性を適用するかどうか、適用する場合はどのように適用するかを表示します。 このプロパティの値は、この列が ID 列であり、 **[永続化されている]** 子プロパティの値と同じかどうかを示します。  
  
> [!NOTE]  
>  **[IDENTITY の指定]** プロパティに対して表示される値を変更するには、このプロパティを展開し、 **[永続化されている]** 子プロパティを編集します。  
  
-   **[永続化されている]** この列が ID 列かどうかを示します。 このプロパティを編集するには、値をクリックしてドロップダウン リストを展開し、別の値を選択します。  
  
-   **[IDENTITY シード]** この ID 列を作成するときに指定されたシード値を表示します。 この値は、テーブルの最初の行に割り当てられます。 このセルを空白にすると、既定により値が 1 に設定されます。 このプロパティを編集するには、値を直接入力します。  
  
-   **[IDENTITY インクリメント]** この ID 列を作成するときに指定された増分値を表示します。 この値は、2 行目以降の各行に対して **[IDENTITY シード]** に加算される増分値です。 このセルを空白にすると、既定により値が 1 に設定されます。 このプロパティを編集するには、値を直接入力します。  
  
 **[インデックス可能]**  
 選択した列にインデックスを作成できるかどうかが表示されます。 たとえば、不明確な計算列にはインデックスを作成できません。  
  
 **[マージ パブリッシュ済み]**  
 列がマージによりパブリッシュされているかどうかが表示されます。  
  
 **[レプリケーションでは使用しない]**  
 レプリケーション時に元の ID 値を保持するかどうかを示します。 レプリケーションの詳細については、「CREATE TABLE」を参照してください。 このプロパティを編集するには、値をクリックしてドロップダウン リストを展開し、別の値を選択します。  
  
 **[レプリケート済み]**  
 この列を別の場所にレプリケートされるかどうかを示します。  
  
 **[RowGuid]**  
 SQL Server が ROWGUID としてその列を使用するかどうかを示します。 一意な ID 列の場合のみ、この値を **[はい]** に設定できます。 このプロパティを編集するには、値をクリックしてドロップダウン リストを展開し、別の値を選択します。  
  
 **サイズ**  
 列のデータ型で許容されるサイズがバイト単位で表示されます。 たとえば、nchar データ型の長さが 10 (文字数) でも、Unicode 文字セットの場合のサイズは 20 になります。  
  
> [!NOTE]  
>  **(max)** のデータ型の長さは行ごとに異なります。 **sp_help** を実行すると、 **(max)** 列の長さとして (-1) が返されます。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] では、列のサイズとして -1 が表示されます。  
  
  