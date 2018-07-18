---
title: 'エラー: ローカル コンピューターでファイアウォールの |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.firewall.localmachine
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
ms.openlocfilehash: e85c97d5950f71d9552bba944450603e47a5ab49
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472868"
---
# <a name="error-firewall-on-local-machine"></a>エラー : ローカル コンピューターのファイアウォール
Visual Studio を実行するローカル コンピューターのインターネット接続ファイアウォールは、リモート デバッグを許可するように設定されていません。 既定のトランスポートを使用したマネージ リモート デバッグまたはネイティブ リモート デバッグでは、DCOM トラフィック用に TCP 135 ポートを開く必要があります。 ファイルおよびプリンターの共有を有効にし、devenv.exe を例外リストに追加することも必要です。 また、IPSEC ポートを開く必要がある場合もあります。  
  
 詳細については、次を参照してください。[リモート デバッグ](../debugger/remote-debugging.md)です。