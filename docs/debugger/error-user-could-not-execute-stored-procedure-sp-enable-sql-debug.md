---
title: 'エラー: ユーザーがいない実行ストアド プロシージャ sp_enable_sql_debug |Microsoft Docs'
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
ms.openlocfilehash: f13eb0b7deb9295ac20e04f4ba1111e128efa0c0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903986"
---
# <a name="error-user-could-not-execute-stored-procedure-spenablesqldebug"></a>エラー : ユーザーがストアド プロシージャ sp_enable_sql_debug を実行できませんでした
ストアド プロシージャ sp_enable_sql_debug がサーバーで実行できません。 考えられる原因を以下に示します。  
  
- 接続の問題。 サーバーへの接続が安定している必要があります。  
  
- サーバーで必要な権限の不足。 SQL Server 2005 でデバッグするには、Visual Studio を実行するアカウントと SQL Server に接続するために使用するアカウントの両方が sysadmin ロールのメンバーであることが必要です。 SQL Server に接続するために使用するアカウントは、使用している Windows ユーザー アカウント (Windows 認証を使用している場合) またはユーザー ID とパスワードが設定されたアカウント (SQL 認証を使用している場合) です。  
  
  詳細については、次を参照してください。[方法: デバッグの SQL Server のアクセス許可設定](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)します。  
  
## <a name="see-also"></a>関連項目  
 [方法: デバッグ用の SQL Server のアクセス許可の設定](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [SQL デバッグの設定](http://msdn.microsoft.com/en-us/3db09e68-edcc-42de-9c22-4e97cfd55ab3)