---
title: フォア グラウンド アプリのデバッグ中にデバッガー ウィンドウを使用して |Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.background
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- foreground program debugging
- remote debugging, debugging foreground programs
- debugging [Visual Studio], while observing foreground programs
- focus, debugging while observing foreground programs
- debugging [Visual Studio], foreground programs
ms.assetid: 9e67a308-1c81-42ab-966b-7fc3c1d2bf7a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 60bd259dd5acb542211fe57b0741c2e28d0baaca
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53910322"
---
# <a name="how-can-i-use-debugger-windows-while-debugging-a-foreground-program"></a>フォアグラウンド プログラムのデバッグ中にデバッガー ウィンドウを使用するには
## <a name="problem-description"></a>問題の説明  
 画面の描画時に発生する問題がデバッグの対象です。 この問題を観察するには、プログラムをフォアグラウンドで実行する必要がありますが、そうするとデバッガー ウィンドウにアクセスできなくなります。 どうしたらいいのでしょうか。  
  
## <a name="solution"></a>ソリューション  
 コンピューターがもう 1 台ある場合は、リモート デバッグを行います。 2 台のコンピューターをセットアップすると、リモート コンピューター上で画面の描画状態を観察しながら、ホスト上でデバッガーを実行できます。 リモート デバッグの詳細については、次を参照してください。[リモート デバッグ](../debugger/remote-debugging.md)します。  
  
## <a name="see-also"></a>「  
 [ネイティブ コードのデバッグに関する FAQ](../debugger/debugging-native-code-faqs.md)   
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)