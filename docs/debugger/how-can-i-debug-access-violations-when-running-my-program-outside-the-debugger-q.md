---
title: "プログラムの実行中にデバッガーの外部で発生するアクセス違反をデバッグするには | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1b8a6e019725f95788b4988fbe1ddef18cb27cc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>プログラムの実行中にデバッガーの外部で発生するアクセス違反をデバッグするには
## <a name="problem-description"></a>問題の説明  
 プログラムが Visual Studio 環境では正しく動作するのに、Windows オペレーティング システムでスタンドアロンで実行するとアクセス違反が発生します。 どのようにデバッグしたらいいのでしょうか。  
  
## <a name="solution"></a>ソリューション  
 設定、[ジャスト イン タイムのデバッグ](../debugger/just-in-time-debugging-in-visual-studio.md)オプションし、アクセス違反が発生するまでは、スタンドアロン プログラムを実行します。 次に、**アクセス違反** ダイアログ ボックスをクリックして**キャンセル**デバッガーを起動します。  
  
 サポート技術情報の文書「How to Locate Where a General Protection (GP) Fault Occurs (Q133174)」も参照してください。 MSDN ライブラリの CD または検索することで、サポート技術情報の記事を検索できます[http://support.microsoft.com/](http://support.microsoft.com/)です。  
  
## <a name="see-also"></a>関連項目  
 [ネイティブ コードのデバッグに関する Faq](../debugger/debugging-native-code-faqs.md)   
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)