---
title: エラー :認証がファイアウォール設定されていません |Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.firewall.noauth
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e565d1372131272f8653df328dbbe9749a8b1ddb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55035303"
---
# <a name="error-firewall-no-authentication"></a>エラー :ファイアウォールの認証が設定されていません
リモート コンピューターのインターネット接続ファイアウォールが、リモート デバッグを許可するように設定されていません。 `No Authentication` を使用してリモート デバッグを実行するには、例外リストに msvsmon.exe を追加する必要があります。 また、IPSEC ポートを開く必要がある場合もあります。  
  
> [!NOTE]
>  リモート デバッガーでは Windows ファイアウォールの自動構成が可能です。 サード パーティのソフトウェア ファイアウォールやハードウェア ファイアウォールなど、Windows ファイアウォール以外のファイアウォールを使用する場合は、リモート デバッグを許可するようにファイアウォールを手動で構成する必要があります。 そのためには、msvsmon.exe がリッスンしている TCP/IP ポートのトラフィックを許可します。 既定では、これらのポートは 4018 と 4019 です。4018 はすべてのオペレーティング システムで使用され、4019 は Windows x64 でのみ使用されます。該当するポートで x86 プロセスのデバッグを許可します。  
  
 詳細については、次を参照してください。[リモート デバッグ](../debugger/remote-debugging.md)します。