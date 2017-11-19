---
title: "フォアグラウンド プログラムのデバッグ中にデバッガー ウィンドウを使用するには | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.background
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
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 08f6b369da587ecb0b4bc9e991bbdcce36235fa8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-can-i-use-debugger-windows-while-debugging-a-foreground-program"></a>フォアグラウンド プログラムのデバッグ中にデバッガー ウィンドウを使用するには
## <a name="problem-description"></a>問題の説明  
 画面の描画時に発生する問題がデバッグの対象です。 この問題を観察するには、プログラムをフォアグラウンドで実行する必要がありますが、そうするとデバッガー ウィンドウにアクセスできなくなります。 どうしたらいいのでしょうか。  
  
## <a name="solution"></a>ソリューション  
 コンピューターがもう 1 台ある場合は、リモート デバッグを行います。 2 台のコンピューターをセットアップすると、リモート コンピューター上で画面の描画状態を観察しながら、ホスト上でデバッガーを実行できます。 リモート デバッグの詳細については、次を参照してください。[リモート デバッグ](../debugger/remote-debugging.md)です。  
  
## <a name="see-also"></a>関連項目  
 [ネイティブ コードのデバッグに関する Faq](../debugger/debugging-native-code-faqs.md)   
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)