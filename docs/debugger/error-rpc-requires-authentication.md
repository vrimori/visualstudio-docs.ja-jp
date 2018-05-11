---
title: 'エラー: 認証を要求する RPC |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.rpc_requires_authentication
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
ms.openlocfilehash: 214dafa5acc925434cf3569570f20ab7f3331bfb
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="error-rpc-requires-authentication"></a>エラー : 認証を要求する RPC
Visual Studio デバッガーは、リモート コンピューターに接続できません。 リモート コンピューター上で、リモート デバッグを制限する RPC ポリシーが有効になっています。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  実行`\` *windir*`\system32\regedt32.exe`  
  
2.  見つけて削除`HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`です。  
  
3.  コンピューターを再起動してレジストリの変更を有効にします。  
  
4.  問題が解決しない場合は、ドメイン管理者に問い合わせて、**コンピューターの構成 > 管理用テンプレート > システム > リモート プロシージャ コール > 認証されていない RPC クライアントの制限**グループ ポリシー設定しています。