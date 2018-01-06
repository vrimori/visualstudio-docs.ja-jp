---
title: "エラー: Transact SQL の実行、デバッグされないで終了 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.error.sqlde_sql_executed_but_not_debugged
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 793e516c334d39cd7befc82a15e793df44d22f3b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Transact-SQL の実行は、デバッグされないで終了しました。
このエラーは、Transact-SQL プロシージャまたは SQLCLR プロシージャをデバッグしようとしたときに、デバッガーが SQL Server からデバッグ メッセージを受信しなかった場合に発生します。  
  
 このエラーは、ネットワークの問題や SQL Server の問題によって発生することもありますが、最も可能性が高いのはアクセス許可の問題です。  
  
 このエラーには、次の 2 つのアカウントが関係します。  
  
-   アプリケーション アカウントは、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] を実行しているユーザー アカウントです。  
  
-   接続アカウントは、SQL Server に接続するために使用される ID です。 接続が SQL 認証を使用している場合、この ID は Visual Studio が実行されている ID と同じであるとは限りません。  
  
 SQL デバッグでは、アプリケーション アカウントが接続アカウントと一致しているか、または sysadmin である必要があります。  
  
 sa などの SQL ログインを使用している場合は、アプリケーション アカウントが sysadmin として SQL Server 上でセットアップされている必要があります。 既定では、SQL サーバーが実行されているコンピューターの管理者は SQL Server の sysadmin です。  
  
 このエラーを解決するには、次の手順を行う必要があります。  
  
-   アクセス許可の設定を確認します。 詳細については、次を参照してください。[する方法: SQL Server アクセス許可の設定をデバッグ用](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)です。  
  
-   SQL デバッグが正しく設定されていることを確認します。  
  
-   ネットワーク管理者またはデータベース管理者に問い合わせます。  
  
## <a name="see-also"></a>参照  
 [SQL デバッグの設定](http://msdn.microsoft.com/en-us/3db09e68-edcc-42de-9c22-4e97cfd55ab3)   
 [方法: デバッグ用の SQL Server のアクセス許可の設定](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [デバッガーの設定と準備](../debugger/debugger-settings-and-preparation.md)   
 [Remote Debugging](../debugger/remote-debugging.md)