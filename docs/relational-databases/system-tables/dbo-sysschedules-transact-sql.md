---
title: dbo.sysschedules (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysschedules_TSQL
- sysschedules
- sysschedules_TSQL
- dbo.sysschedules
dev_langs:
- TSQL
helpviewer_keywords:
- sysschedules system table
ms.assetid: 4cac9237-7a69-4035-bb3e-928b76aad698
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5a1922fd8b9cdfb327186afe453fc1904d698579
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47674380"
---
# <a name="dbosysschedules-transact-sql"></a>dbo.sysschedules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのジョブ スケジュールに関する情報を格納します。 このテーブルに格納されます、 **msdb**データベース。  
  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**schedule_id**|**int**|ID、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント ジョブのスケジュール。|  
|**schedule_uid**|**uniqueidentifier**|ジョブ スケジュールの一意識別子。 この値は分散ジョブのスケジュールを識別するために使用されます。|  
|**originating_server_id**|**int**|ジョブ スケジュールを取得したマスター サーバーの ID。|  
|**name**|**sysname (nvarchar(128))**|ジョブ スケジュールのユーザー定義名。 名前はジョブ内で一意であることが必要です。|  
|**owner_sid**|**varbinary(85)**|Microsoft Windows *security_identifier*のユーザーまたはジョブのスケジュールを所有しているグループ。|  
|**enabled**|**int**|ジョブ スケジュールのステータス。<br /><br /> **0**になっていません。<br /><br /> **1** = 有効にします。<br /><br /> スケジュールが無効な場合、そのスケジュールでジョブは実行されません。|  
|**freq_type**|**int**|このスケジュールでジョブを実行する間隔。<br /><br /> **1** = 1 回のみ<br /><br /> **4** = 毎日<br /><br /> **8** = 毎週<br /><br /> **16**毎月を =<br /><br /> **32**を基準とする、毎月を = **freq_interval**<br /><br /> **64** SQL Server エージェント サービスの起動時に実行を =<br /><br /> **128**コンピューターがアイドル状態のときに実行を =|  
|**freq_interval**|**int**|ジョブを実行する日数。 値に依存**freq_type**します。 既定値は**0**、ことを示します**freq_interval**は使用されません。 使用可能な値とその影響は、以下の表を参照してください。|  
|**freq_subday_type**|**int**|単位、 **freq_subday_interval**します。 使用可能な値とその説明を次に示します。<br /><br /> <br /><br /> **1** : 指定された時刻<br /><br /> **2** : 秒<br /><br /> **4** : 分<br /><br /> **8** : 時間|  
|**freq_subday_interval**|**int**|数**freq_subday_type**にジョブの各実行間に発生する期間。|  
|**freq_relative_interval**|**int**|ときに**freq_interval** 、各月場合に発生します**freq_interval**は**32** (月単位)。 次の値のいずれかです。<br /><br /> **0** = **freq_relative_interval**は使用されません<br /><br /> **1**最初を =<br /><br /> **2**秒を =<br /><br /> **4** = サード<br /><br /> **8**第 4 を =<br /><br /> **16**最後を =|  
|**freq_recurrence_**<br /><br /> **factor**|**int**|週または月を単位とした、ジョブの予定実行間隔。 **freq_recurrence_factor**場合にのみ使用が**freq_type**は**8**、 **16**、または**32**します。 この列が含まれている場合**0**、 **freq_recurrence_factor**は使用されません。|  
|**active_start_date**|**int**|ジョブの実行を開始できる日付。 日付は yyyymmdd です。 NULL は今日の日付を表します。|  
|**active_end_date**|**int**|ジョブの実行を停止できる日付。 日付の形式は YYYYMMDD です。|  
|**active_start_time**|**int**|間の日で時間**active_start_date**と**active_end_date**そのジョブが実行を開始します。 時刻の形式は HHMMSS で、24 時間形式です。|  
|**active_end_time**|**int**|間の日で時間**active_start_date**と**active_end_date**そのジョブが実行を停止します。 時刻の形式は HHMMSS で、24 時間形式です。|  
|**date_created**|**datetime**|スケジュールを作成した日付と時刻。|  
|**date_modified**|**datetime**|スケジュールを最後に変更した日付と時刻。|  
|**version_number**|**int**|スケジュールの現在のバージョン番号。 たとえば、スケジュールに 10 回が変更された場合、 **version_number** 10。|  
  
|freq_type の値|freq_interval への影響|  
|-------------------------|------------------------------|  
|**1** (1 回)|**freq_interval**は使用されません (**0**)|  
|**4** (毎日)|すべて**freq_interval**日|  
|**8** (毎週)|**freq_interval**は、次の 1 つ以上。<br /><br /> **1**日曜日を =<br /><br /> **2** = 月曜日<br /><br /> **4** = 火曜日<br /><br /> **8** = 水曜日<br /><br /> **16** = 木曜日<br /><br /> **32** = 金曜日<br /><br /> **64** = 土曜日|  
|**16** (毎月)|**Freq_interval**します月の日|  
|**32** (月単位、相対)|**freq_interval**は、次の 1 つです。<br /><br /> **1**日曜日を =<br /><br /> **2** = 月曜日<br /><br /> **3** = 火曜日<br /><br /> **4** = 水曜日<br /><br /> **5** = 木曜日<br /><br /> **6** = 金曜日<br /><br /> **7** = 土曜日<br /><br /> **8** = 日<br /><br /> **9** = 平日<br /><br /> **10** = 土日|  
|**64** (SQL Server エージェント サービスの起動時に開始します)|**freq_interval**は使用されません (**0**)|  
|**128** (コンピューターがアイドル状態のときに実行されます)|**freq_interval**は使用されません (**0**)|  
  
## <a name="see-also"></a>関連項目  
 [では&#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/dbo-sysjobschedules-transact-sql.md)  
  
  
