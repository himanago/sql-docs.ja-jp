---
title: "キューブ スキーマの表示 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82fc715c-e08e-447d-8fc8-9c9005f145f0
caps.latest.revision: 8
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 7a46b1e284d2f75a22f7ac21b0353872db7108a1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="view-the-cube-schema"></a>キューブ スキーマの表示
  **キューブ デザイナー** の **[キューブ構造]** タブにある **[データ ソース ビュー]** ペインには、キューブ スキーマが表示されます。 スキーマとは、キューブのメジャーおよびディメンションの派生元であるテーブルのセットです。 どのキューブ スキーマも、キューブ内のメジャーとディメンションの基になっている 1 つ以上のファクト テーブルと 1 つ以上のディメンション テーブルで構成されます。  
  
 **[キューブ構造]** タブの **[データ ソース ビュー]** ペインには、キューブの基になっているデータ ソース ビューのダイアグラムが表示されます。 このダイアグラムは、データ ソース ビューのメイン ダイアグラムのサブセットです。 **[データ ソース ビュー]** ペインのテーブルの表示と非表示を切り替えたり、既存のダイアグラムを表示したりできます。 ただし、基になるスキーマに変更 (新しいリレーションシップまたは名前付きクエリの追加など) を加えることはできません。 スキーマに変更を加えるには、データ ソース ビュー デザイナーを使用します。  
  
 キューブを作成すると、 **[キューブ構造]** タブの **[データ ソース ビュー]** ペインに最初に表示されるダイアグラムは、プロジェクトまたはデータベースのデータ ソース ビューの **[すべてのテーブルを表示]** ダイアグラムと同じになります。 このダイアグラムをデータ ソース ビューの既存のダイアグラムで置換して、 **[データ ソース ビュー]** ペインで調整を加えることができます。  
  
 **キューブ デザイナー**でダイアグラムを編集する場合、タブまたはタブ内の選択したオブジェクトに対して実行できるコマンドは、 **[データ ソース ビュー]** メニューから選択できます。 また、ダイアグラムまたはダイアグラム内の任意のオブジェクトの背景を右クリックして、ダイアグラムまたは選択したオブジェクトに対してコマンドを実行することもできます。 可能な代替手段としては以下の方法があります。  
  
-   ダイアグラム形式とツリー形式の切り替え  
  
-   テーブルの整列、検索、表示、および非表示  
  
-   表示名の表示  
  
-   レイアウトの切り替え  
  
-   倍率の変更  
  
-   プロパティの表示  
  
 さらに、次の表に示す操作を実行することもできます。  
  
|変換先|方法|  
|--------|-------------|  
|キューブのデータ ソース ビューのダイアグラムを使用する|**[データ ソース ビュー]** メニューの **[ダイアグラムのコピー元]**をポイントして、使用するデータ ソース ビュー ダイアグラムをクリックします。<br /><br /> - または -<br /><br /> **[データ ソース ビュー]** ペインの背景を右クリックして、 **[ダイアグラムのコピー元]**をポイントし、使用するデータ ソース ビューのダイアグラムをクリックします。 この方法では、ダイアグラムの独立したコピーが作成されるため、 **[キューブ ビルダー]** タブで加えた変更は元のダイアグラムには反映されません。|  
|キューブで使用されているテーブルのみを表示する|**[データ ソース ビュー]** メニューの **[使用されたテーブルのみを表示]**をクリックします。<br /><br /> - または -<br /><br /> **[データ ソース ビュー]** ペインの背景を右クリックして、 **[使用されたテーブルのみを表示]**をクリックします。|  
|データ ソース ビューのスキーマを編集する|**[データ ソース ビュー]** メニューで、 **[データ ソース ビューの編集]**をクリックします。<br /><br /> - または -<br /><br /> **[データ ソース ビュー]** ペインの背景を右クリックして、 **[データ ソース ビューの編集]**をクリックします。|  
  
  