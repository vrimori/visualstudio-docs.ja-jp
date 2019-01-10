---
title: エラー :ユーザーがいない実行ストアド プロシージャ sp_enable_sql_debug |Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
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
ms.openlocfilehash: 9c80a4055b899f155b4be8e7832df9f3aa22db20
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53903579"
---
# <a name="error-user-could-not-execute-stored-procedure-spenablesqldebug"></a>エラー :ユーザーがストアド プロシージャ sp_enable_sql_debug を実行できませんでした

ストアド プロシージャ sp_enable_sql_debug がサーバーで実行できません。 考えられる原因を以下に示します。

- 接続の問題。 サーバーへの接続が安定している必要があります。

- サーバーで必要な権限の不足。 SQL Server 2005 でデバッグするには、Visual Studio を実行するアカウントと SQL Server に接続するために使用するアカウントの両方が sysadmin ロールのメンバーであることが必要です。 SQL Server に接続するために使用するアカウントは、使用している Windows ユーザー アカウント (Windows 認証を使用している場合) またはユーザー ID とパスワードが設定されたアカウント (SQL 認証を使用している場合) です。

詳細については、「[方法 :デバッグ用の SQL Server のアクセス許可の設定](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)します。

## <a name="see-also"></a>「

- [方法: デバッグ用の SQL Server のアクセス許可を設定します。](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [SQL デバッグの設定](/previous-versions/visualstudio/visual-studio-2010/s4sszxst\(v\=vs.100\))