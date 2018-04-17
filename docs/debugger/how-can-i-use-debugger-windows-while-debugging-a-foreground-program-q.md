---
title: フォアグラウンド プログラムのデバッグ中にデバッガー ウィンドウを使用するには | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
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
ms.openlocfilehash: 649ab634f826f633559f264a78ff356a65f74818
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-can-i-use-debugger-windows-while-debugging-a-foreground-program"></a>フォアグラウンド プログラムのデバッグ中にデバッガー ウィンドウを使用するには
## <a name="problem-description"></a>問題の説明  
 画面の描画時に発生する問題がデバッグの対象です。 この問題を観察するには、プログラムをフォアグラウンドで実行する必要がありますが、そうするとデバッガー ウィンドウにアクセスできなくなります。 どうしたらいいのでしょうか。  
  
## <a name="solution"></a>ソリューション  
 コンピューターがもう 1 台ある場合は、リモート デバッグを行います。 2 台のコンピューターをセットアップすると、リモート コンピューター上で画面の描画状態を観察しながら、ホスト上でデバッガーを実行できます。 リモート デバッグの詳細については、次を参照してください。[リモート デバッグ](../debugger/remote-debugging.md)です。  
  
## <a name="see-also"></a>関連項目  
 [ネイティブ コードのデバッグに関する Faq](../debugger/debugging-native-code-faqs.md)   
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)