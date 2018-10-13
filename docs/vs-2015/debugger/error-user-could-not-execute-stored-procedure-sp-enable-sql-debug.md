---
title: 'エラー: ユーザーがいない実行ストアド プロシージャ sp_enable_sql_debug |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.sqlde_accessdenied
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 11957495-c238-4cc5-8937-e4026f5e10e1
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b732c7d562c97e1043bb6dc62bba7d3a405227b9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49254014"
---
# <a name="error-user-could-not-execute-stored-procedure-spenablesqldebug"></a>エラー : ユーザーがストアド プロシージャ sp_enable_sql_debug を実行できませんでした
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ストアド プロシージャ sp_enable_sql_debug がサーバーで実行できません。 考えられる原因を以下に示します。  
  
-   接続の問題。 サーバーへの接続が安定している必要があります。  
  
-   サーバーで必要な権限の不足。 SQL Server 2005 でデバッグするには、Visual Studio を実行するアカウントと SQL Server に接続するために使用するアカウントの両方が sysadmin ロールのメンバーであることが必要です。 SQL Server に接続するために使用するアカウントは、使用している Windows ユーザー アカウント (Windows 認証を使用している場合) またはユーザー ID とパスワードが設定されたアカウント (SQL 認証を使用している場合) です。  
  
 詳細については、次を参照してください。[方法: デバッグの SQL Server のアクセス許可設定](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)します。  
  
## <a name="see-also"></a>関連項目  
 [方法: デバッグ用の SQL Server のアクセス許可の設定](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [SQL デバッグの設定](http://msdn.microsoft.com/en-us/3db09e68-edcc-42de-9c22-4e97cfd55ab3)



