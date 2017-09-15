---
title: "レポート (SSRS) にコードを追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code [Reporting Services]
- custom code [Reporting Services]
- expressions [Reporting Services], code
- adding code
- reports [Reporting Services], code
ms.assetid: 00ef8fc6-99fe-49b2-8a22-7eb475881dc4
caps.latest.revision: 41
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ae58ddb9260037fafa37263050e55681944738eb
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="add-code-to-a-report-ssrs"></a>レポートにコードを追加する (SSRS)
  どの式でも独自のカスタム コードを呼び出すことができます。 次の 2 つの方法でコードを提供できます。  
  
-   [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] で記述されたコードをレポートに直接埋め込みます。 コードが [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] または <xref:System.Math> ではない <xref:System.Convert>を参照する場合は、レポートへの参照を追加する必要があります。 詳細については、「[レポートにアセンブリへの参照を追加する (SSRS)](../../reporting-services/report-design/add-an-assembly-reference-to-a-report-ssrs.md)」を参照してください。 コードから行うことのできる参照の詳細については、「[レポート デザイナーでカスタム コードやアセンブリを式から参照する (SSRS)](../../reporting-services/report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)」を参照してください。  
  
-   [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] を使用して、カスタム コード アセンブリを指定します。 カスタム アセンブリを指定する場合、レポートの作成場所のコンピューターとレポートを表示するレポート サーバーの両方にそれをインストールする必要があります。 詳細については、「 [レポートでのカスタム アセンブリの使用](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)」を参照してください。  
  
### <a name="to-add-embedded-code-to-a-report"></a>レポートに埋め込みコードを追加するには  
  
1.  **[デザイン]** ビューで、デザイン画面のレポートの罫線の外を右クリックし、 **[レポートのプロパティ]**をクリックします。  
  
2.  **[コード]**をクリックします。  
  
3.  **[カスタム コード]**でコードを入力します。 コード内にエラーがあると、レポートの実行時に警告が生成されます。 次の例では、" `ChangeWord` " という単語を "`Bike`" で置き換える`Bicycle`という名前のカスタム関数が作成されます。  
  
    ```  
    Public Function ChangeWord(ByVal s As String) As String  
       Dim strBuilder As New System.Text.StringBuilder(s)  
       If s.Contains("Bike") Then  
          strBuilder.Replace("Bike", "Bicycle")  
          Return strBuilder.ToString()  
          Else : Return s  
       End If  
    End Function  
    ```  
  
4.  次の例は、式で Category という名前のデータセット フィールドをこの関数に渡す方法を示しています。  
  
    ```  
    =Code.ChangeWord(Fields!Category.Value)  
    ```  
  
     この式をカテゴリの値を表示するテーブル セルに追加すると、"Bike" という単語がその行のデータセット フィールドに現れるたびに、テーブル セルの値は "Bicycle" という単語を表示します。  
  
## <a name="see-also"></a>参照  
 [レポートのプロパティ」 ダイアログ ボックスのコード](http://msdn.microsoft.com/library/955d4b11-17b4-4f1c-9690-6e7af54caea7)   
 [式の例と &#40; です。レポート ビルダーおよび SSRS &#41; です。](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Parameters コレクションの参照と &#40; です。レポート ビルダーおよび SSRS &#41; です。](../../reporting-services/report-design/built-in-collections-parameters-collection-references-report-builder.md)  
  
  