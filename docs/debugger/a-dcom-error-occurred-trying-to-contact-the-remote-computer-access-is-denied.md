---
title: "リモート コンピューターにアクセスしようとしたときに DCOM エラーが発生しました。 アクセスが拒否されました。 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.remote.dcom_access_denied
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, DCOM error
- remote DCOM access denied error
- DCOM, access errors
ms.assetid: 9d7dfc1b-9fe0-4f54-9c50-9c0e0f8358c5
caps.latest.revision: "27"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fe153a5252603cf967b396932a6479a8df437a08
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>リモート コンピューターにアクセスしようとしたときに DCOM エラーが発生しました。 アクセスが拒否されました。
リモート デバッグでは、DCOM を使用して次のような状況でローカル コンピューターとリモート コンピューターとの間で通信します。  
  
-   デバッガーに設定されている**ネイティブ互換モード**または**マネージ互換モード**がオンになって、**ツール > オプション > デバッグ**ページ  
  
-   マネージ C++ (C + +/CLI) コードをデバッグする場合。  
  
-   Visual Studio 2013 でとき**ネイティブのエディット コンティニュを有効にする**がオンになって、**ツール > オプション > デバッグ**ページ  
  
-   一部のサード パーティのデバッグ シナリオ  
  
 このエラーが発生するのは、Visual Studio のプロセスが DCOM 経由でリモート デバッガープロセスに対して自己認証できない (入力した資格情報が不十分と見なされた) 場合です。 次のいずれかの回避策で問題を解決できることがあります。  
  
-   **[ネイティブ互換モード]** と **[マネージ互換モード]**をオフにします。  
  
-   Visual Studio 2013 で、 **[ネイティブのエディット コンティニュを有効にする]**をオフにします。  
  
-   両方のコンピューターを再起動する。  
  
-   リモート デバッグで資格情報の入力が必要な場合は、資格情報の保存のチェック ボックスをオンにする。  
  
## <a name="see-also"></a>関連項目  
 [リモート デバッグ エラーとトラブルシューティング](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)