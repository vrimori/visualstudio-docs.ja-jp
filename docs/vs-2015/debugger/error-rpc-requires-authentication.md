---
title: 'エラー: 認証を要求する RPC |Microsoft Docs'
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
ms.openlocfilehash: 5643e815386541bb9045eb56cacbd68e7e9b998d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49193837"
---
# <a name="error-rpc-requires-authentication"></a>エラー : 認証を要求する RPC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio デバッガーは、リモート コンピューターに接続できません。 リモート コンピューター上で、リモート デバッグを制限する RPC ポリシーが有効になっています。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  実行`\` *windir*`\system32\regedt32.exe`  
  
2.  見つけて削除`HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`します。  
  
3.  コンピューターを再起動してレジストリの変更を有効にします。  
  
4.  問題が解決しない場合について、ドメイン管理者に問い合わせて、**コンピューターの構成 -> 管理用テンプレート - > システム]、[リモート プロシージャ呼び出しに認証されていない RPC クライアントの制限]-> [** グループポリシーの設定。



