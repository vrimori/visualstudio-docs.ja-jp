---
title: 'エラー: TRANSACT-SQL の実行、デバッグされないで終了 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1bc4de5e9ef0830f69b60d773a59411c4b691454
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894756"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Transact-SQL の実行は、デバッグされないで終了しました。
このエラーは、Transact-SQL プロシージャまたは SQLCLR プロシージャをデバッグしようとしたときに、デバッガーが SQL Server からデバッグ メッセージを受信しなかった場合に発生します。  
  
 このエラーは、ネットワークの問題や SQL Server の問題によって発生することもありますが、最も可能性が高いのはアクセス許可の問題です。  
  
 このエラーには、次の 2 つのアカウントが関係します。  
  
- アプリケーション アカウントは、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] を実行しているユーザー アカウントです。  
  
- 接続アカウントは、SQL Server に接続するために使用される ID です。 接続が SQL 認証を使用している場合、この ID は Visual Studio が実行されている ID と同じであるとは限りません。  
  
  SQL デバッグでは、アプリケーション アカウントが接続アカウントと一致しているか、または sysadmin である必要があります。  
  
  sa などの SQL ログインを使用している場合は、アプリケーション アカウントが sysadmin として SQL Server 上でセットアップされている必要があります。 既定では、SQL サーバーが実行されているコンピューターの管理者は SQL Server の sysadmin です。  
  
  このエラーを解決するには、次の手順を行う必要があります。  
  
- アクセス許可の設定を確認します。 詳細については、次を参照してください。[方法: デバッグの SQL Server のアクセス許可設定](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)します。  
  
- SQL デバッグが正しく設定されていることを確認します。  
  
- ネットワーク管理者またはデータベース管理者に問い合わせます。  
  
## <a name="see-also"></a>関連項目  
 [SQL デバッグの設定](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))   
 [方法: デバッグ用の SQL Server のアクセス許可の設定](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [デバッガーの設定と準備](../debugger/debugger-settings-and-preparation.md)   
 [Remote Debugging](../debugger/remote-debugging.md)