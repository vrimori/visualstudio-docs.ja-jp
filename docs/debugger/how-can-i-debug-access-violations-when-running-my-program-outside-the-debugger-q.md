---
title: プログラムの実行中にデバッガーの外部で発生するアクセス違反をデバッグするには | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9f3e4a79ba90f887f11c3fd9a7bddf318ace35cc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>プログラムの実行中にデバッガーの外部で発生するアクセス違反をデバッグするには
## <a name="problem-description"></a>問題の説明  
 プログラムが Visual Studio 環境では正しく動作するのに、Windows オペレーティング システムでスタンドアロンで実行するとアクセス違反が発生します。 どのようにデバッグしたらいいのでしょうか。  
  
## <a name="solution"></a>ソリューション  
 設定、[ジャスト イン タイムのデバッグ](../debugger/just-in-time-debugging-in-visual-studio.md)オプションし、アクセス違反が発生するまでは、スタンドアロン プログラムを実行します。 次に、**アクセス違反** ダイアログ ボックスをクリックして**キャンセル**デバッガーを起動します。  
  
## <a name="see-also"></a>関連項目  
 [ネイティブ コードのデバッグに関する Faq](../debugger/debugging-native-code-faqs.md)   
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)