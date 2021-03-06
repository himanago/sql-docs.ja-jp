---
title: SQL Server Management Studio - テレメトリ(SSMS) | Microsoft Docs
ms.custom: ''
ms.date: 02/20/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: c28ffa44-7b8b-4efa-b755-c7a3b1c11ce4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 70c044c6b674ef7b64368edfbee069cf6c6a6332
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51698901"
---
# <a name="local-audit-for-ssms-usage-feedback-collection"></a>SSMS Usage Feedback Collection の Local Audit
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
SQL Server Management Studio (SSMS) には、匿名の機能使用状況データを収集して Microsoft に送信する、インターネット対応機能が含まれています。 SSMS は、標準的なコンピューター情報、および使用とパフォーマンスに関する情報を収集する場合があります。これらの情報は Microsoft に送信され、SSMS の品質、セキュリティ、および信頼性を向上させる目的で分析されます。 お客様の名前、住所などの連絡先情報は収集されません。 詳細については、[SQL Server のプライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkID=868444)をご覧ください。

## <a name="audit-feature-usage-data"></a>Audit 機能の使用状況データ

SSMS で収集される機能の使用状況データを表示するには、次の操作を行います。
1.  SSMS を起動します。
2.  メインメニューで **[ビュー]**、**[出力]** の順にクリックし、**[出力]** ウィンドウを表示します。 
3.  **[出力]** ウィンドウが表示されたら、**[出力元の表示:]** メニューで **[テレメトリ]** を選択します。

SSMS を使用してデータベースと対話している間に、収集されたデータが **[出力]** ウィンドウに表示されます。

## <a name="enable-or-disable-usage-feedback-collection-in-ssms"></a>SSMS の使用状況のフィードバックの収集を有効または無効にする

SSMS の使用状況データの収集を有効または無効にするには、「[Microsoft にフィードバックを送信するように SQL Server 2016 を構成する方法](https://support.microsoft.com/help/3153756/how-to-configure-sql-server-2016-to-send-feedback-to-microsoft)」をご覧ください。

## <a name="see-also"></a>参照

[SQL Server Usage Feedback Collection の Local Audit](https://msdn.microsoft.com/library/mt743085.aspx)
