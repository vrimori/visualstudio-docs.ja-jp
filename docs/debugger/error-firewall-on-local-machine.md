---
title: "エラー: ローカル コンピューターでファイアウォールの |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.error.firewall.localmachine
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 160e71e357046b69019323ada5ff9cde006460bc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="error-firewall-on-local-machine"></a>エラー : ローカル コンピューターのファイアウォール
Visual Studio を実行するローカル コンピューターのインターネット接続ファイアウォールは、リモート デバッグを許可するように設定されていません。 既定のトランスポートを使用したマネージ リモート デバッグまたはネイティブ リモート デバッグでは、DCOM トラフィック用に TCP 135 ポートを開く必要があります。 ファイルおよびプリンターの共有を有効にし、devenv.exe を例外リストに追加することも必要です。 また、IPSEC ポートを開く必要がある場合もあります。  
  
 詳細については、次を参照してください。[リモート デバッグ](../debugger/remote-debugging.md)です。