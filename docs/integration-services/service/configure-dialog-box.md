---
title: "[構成] ダイアログ ボックス |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.configure.f1
- sql13.SSIS.SSMS.ISPROJECTPROP.REFERENCES.F1
- sql13.SSIS.SSMS.ISPROJECTPROP.PARAMETERS.F1
ms.assetid: 10183c8d-b1be-420f-972a-96ea97d4f4d8
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f9587abfb97ec048985ac28de0e7dc585e2bea61
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="configure-dialog-box"></a>[構成] ダイアログ ボックス
  パッケージとプロジェクトのパラメーター、接続マネージャー、および環境への参照を構成するには、 **[構成]** ダイアログ ボックスを使用します。  
  
 **目的に合ったトピックをクリックしてください**  
  
-   [[構成] ダイアログ ボックスを開く](#open_dialog)  
  
-   [[パラメーター] ページのオプションの設定](#parameter)  
  
-   [[参照] ページのオプションの設定](#references)  
  
##  <a name="open_dialog"></a> [構成] ダイアログ ボックスを開く  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]から [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに接続します。  
  
     SSISDB データベースをホストする [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続されます。  
  
2.  オブジェクト エクスプローラーで、ツリーを展開して、 **[Integration Services カタログ]** ノードを表示します。  
  
3.  **[SSISDB]** ノードを展開します。  
  
4.  構成するパッケージまたはプロジェクトが格納されているフォルダーを展開します。  
  
5.  パッケージまたはプロジェクトを右クリックし、 **[構成]**をクリックします。  
  
##  <a name="parameter"></a> [パラメーター] ページのオプションの設定  
 パラメーターの名前と値を表示したり、値を変更するには、 **[パラメーター]** ページを使用します。  
  
 **[スコープ]** ボックスの一覧から、 **[パラメーター]** タブと **[接続マネージャー]** タブに表示されるパラメーターのスコープを選択します。  
  
 **[パラメーター]** タブのオプションの一覧を次に示します。  
  
 **コンテナー**  
 パラメーターを含むオブジェクトを一覧表示します。  
  
 **名前**  
 パラメーター名を一覧表示します。  
  
 **Value**  
 パラメーター値を一覧表示します。 **[パラメーター値の設定]** ダイアログ ボックスの値を変更するには、参照ボタンをクリックします。  
  
 **[接続マネージャー]** タブのオプションの一覧を次に示します。 このタブは、接続マネージャーのプロパティの値を変更するときに使用します。 パラメーターは、SSIS サーバー上でプロパティ用に自動的に生成されます。  
  
 **コンテナー**  
 接続マネージャーを含むオブジェクトを一覧表示します。  
  
 **名前**  
 接続マネージャーの名前を一覧表示します。  
  
 **プロパティ名**  
 接続マネージャーのプロパティの名前を一覧表示します。  
  
 **値**  
 接続マネージャーのプロパティに割り当てられた値を一覧表示します。 **[パラメーター値の設定]** ダイアログ ボックスの値を変更するには、参照ボタンをクリックします。 リテラル値を入力するか、使用する値を含んでいる環境変数をマップするか、パッケージの既定値を使用することができます。  
  
##  <a name="references"></a> [参照] ページのオプションの設定  
 環境への参照を追加および削除したり、環境プロパティにアクセスするには、 **[参照]** ページを使用します。  
  
 環境は、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに配置したプロジェクトに含まれるパッケージのランタイム値を示します。  
  
 **環境**  
 環境を一覧表示します。  
  
 **環境フォルダー**  
 環境を含むフォルダーを一覧表示します。  
  
 **開く**  
 **[環境のプロパティ]** ダイアログ ボックスを開く場合にクリックします。  
  
 **[追加]**  
 環境への参照を追加する場合にクリックします。 **[環境の参照]** ダイアログ ボックスで、環境をクリックして **[OK]**をクリックします。  
  
 **SSISDB** ノードの下の任意のプロジェクト フォルダーに含まれている環境を選択できます。  
  
 **[削除]**  
 **[参照]** 領域に表示されている環境を選択し、 **[削除]**をクリックします。  
  
  