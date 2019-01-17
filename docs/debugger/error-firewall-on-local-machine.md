---
title: エラー :ローカル コンピューターのファイアウォール |Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: d2fafd14a816f75ac4acdf4de7db0ceda1430652
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53919840"
---
# <a name="error-firewall-on-local-machine"></a>エラー :ローカル コンピューターのファイアウォール
Visual Studio を実行するローカル コンピューターのインターネット接続ファイアウォールは、リモート デバッグを許可するように設定されていません。 既定のトランスポートを使用したマネージド リモート デバッグまたはネイティブ リモート デバッグでは、DCOM トラフィック用に TCP 135 ポートを開く必要があります。 ファイルおよびプリンターの共有を有効にし、devenv.exe を例外リストに追加することも必要です。 また、IPSEC ポートを開く必要がある場合もあります。  
  
 詳細については、次を参照してください。[リモート デバッグ](../debugger/remote-debugging.md)します。