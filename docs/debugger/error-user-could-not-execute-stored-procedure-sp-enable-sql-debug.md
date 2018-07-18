---
title: 'エラー: ユーザーがいない実行ストアド プロシージャ sp_enable_sql_debug |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.sqlde_accessdenied
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e36c56f594b9858334f3b67042183278afa218df
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472424"
---
# <a name="error-user-could-not-execute-stored-procedure-spenablesqldebug"></a>エラー : ユーザーがストアド プロシージャ sp_enable_sql_debug を実行できませんでした
ストアド プロシージャ sp_enable_sql_debug がサーバーで実行できません。 考えられる原因を以下に示します。  
  
-   接続の問題。 サーバーへの接続が安定している必要があります。  
  
-   サーバーで必要な権限の不足。 SQL Server 2005 でデバッグするには、Visual Studio を実行するアカウントと SQL Server に接続するために使用するアカウントの両方が sysadmin ロールのメンバーであることが必要です。 SQL Server に接続するために使用するアカウントは、使用している Windows ユーザー アカウント (Windows 認証を使用している場合) またはユーザー ID とパスワードが設定されたアカウント (SQL 認証を使用している場合) です。  
  
 詳細については、次を参照してください。[する方法: SQL Server アクセス許可の設定をデバッグ用](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)です。  
  
## <a name="see-also"></a>関連項目  
 [方法: デバッグ用の SQL Server のアクセス許可の設定](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [SQL デバッグの設定](http://msdn.microsoft.com/en-us/3db09e68-edcc-42de-9c22-4e97cfd55ab3)