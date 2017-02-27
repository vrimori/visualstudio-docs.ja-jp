---
title: "エラー : ユーザーがストアド プロシージャ sp_enable_sql_debug を実行できませんでした | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.sqlde_accessdenied"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 11957495-c238-4cc5-8937-e4026f5e10e1
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# エラー : ユーザーがストアド プロシージャ sp_enable_sql_debug を実行できませんでした
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ストアド プロシージャ sp\_enable\_sql\_debug がサーバーで実行できません。  考えられる原因を以下に示します。  
  
-   接続の問題。  サーバーへの接続が安定している必要があります。  
  
-   サーバーで必要な権限の不足。  SQL Server 2005 でデバッグするには、Visual Studio を実行するアカウントと SQL Server に接続するために使用するアカウントの両方が sysadmin ロールのメンバーであることが必要です。  SQL Server に接続するために使用するアカウントは、使用している Windows ユーザー アカウント \(Windows 認証を使用している場合\) またはユーザー ID とパスワードが設定されたアカウント \(SQL 認証を使用している場合\) です。  
  
 詳細については、「[How to: Set SQL Server Permissions for Debugging](http://msdn.microsoft.com/ja-jp/84e088d0-0409-41d4-841b-f5d4b0fda414)」を参照してください。  
  
## 参照  
 [How to: Set SQL Server Permissions for Debugging](http://msdn.microsoft.com/ja-jp/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Setting Up SQL Debugging](http://msdn.microsoft.com/ja-jp/3db09e68-edcc-42de-9c22-4e97cfd55ab3)