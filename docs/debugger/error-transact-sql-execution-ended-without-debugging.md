---
title: エラー :Transact SQL の実行、デバッグされないで終了 |Microsoft Docs
ms.date: 11/08/2018
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.sqlde_sql_executed_but_not_debugged
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 17c1854826de2314dfe8124d99f6ec6c8899ee70
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55011222"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>エラー :Transact-SQL の実行は、デバッグされないで終了しました

このエラーは、TRANSACT-SQL または SQLCLR プロシージャをデバッグしようとしているし、デバッガーは、SQL Server からのデバッグ メッセージを受信しないときに発生します。  
  
この問題はネットワークの問題のため、または SQL Server では、上の問題になりますが、最も一般的な原因は、アクセス許可の問題。  
  
このエラーには、次の 2 つのアカウントが関係します。  
  
- アプリケーション アカウントは、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] を実行しているユーザー アカウントです。  
  
- 接続アカウントは、SQL Server に接続するために使用される ID です。 このアカウントは、接続は SQL 認証を使用している場合、Visual Studio を実行している id と同じでないとは限りません。  
  
  SQL デバッグでは、アプリケーション アカウントが接続アカウントと同じか、sysadmin であること必要があります。  
  
  Sa のような SQL アカウント名を使用している場合、アプリケーション アカウントする必要がありますとして設定する、SQL server sysadmin。 既定では、SQL server がで実行されているコンピューターの管理者は、SQL Server の sysadmin は。  
  
  このエラーを解決するには、次の手順を行う必要があります。  
  
  - アクセス許可の設定を確認します。 詳細については、「[方法 :デバッグ用の SQL Server のアクセス許可の設定](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)します。  
  
  - SQL デバッグが正しく設定されていることを確認します。  
  
  - ネットワーク管理者またはデータベース管理者に問い合わせます。  
  
## <a name="see-also"></a>関連項目

- [SQL デバッグの設定](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))
- [方法: デバッグ用の SQL Server のアクセス許可を設定します。](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [デバッガーの設定と準備](../debugger/debugger-settings-and-preparation.md)
- [Remote Debugging](../debugger/remote-debugging.md)
