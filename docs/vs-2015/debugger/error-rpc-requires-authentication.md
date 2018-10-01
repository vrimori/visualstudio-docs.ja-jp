---
title: 'エラー: 認証を要求する RPC |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.rpc_requires_authentication
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 88362b3b-8fbe-431f-96a4-80e2d822bbc7
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e606c0e730b279723248a3fdbdd5b3e2bca1c4a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536232"
---
# <a name="error-rpc-requires-authentication"></a>エラー : 認証を要求する RPC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[エラー: RPC は認証が必要](https://docs.microsoft.com/visualstudio/debugger/error-rpc-requires-authentication)します。  
  
Visual Studio デバッガーは、リモート コンピューターに接続できません。 リモート コンピューター上で、リモート デバッグを制限する RPC ポリシーが有効になっています。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  実行`\` *windir*`\system32\regedt32.exe`  
  
2.  見つけて削除`HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`します。  
  
3.  コンピューターを再起動してレジストリの変更を有効にします。  
  
4.  問題が解決しない場合について、ドメイン管理者に問い合わせて、**コンピューターの構成 -> 管理用テンプレート - > システム]、[リモート プロシージャ呼び出しに認証されていない RPC クライアントの制限]-> [** グループポリシーの設定。



