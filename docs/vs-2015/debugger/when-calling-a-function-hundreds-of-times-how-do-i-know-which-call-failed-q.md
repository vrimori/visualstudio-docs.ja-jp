---
title: ある関数が何回も呼び出される場合、どの呼び出しでエラーが発生するのかを調べるには | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.functions
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- conditional breakpoints
- errors [debugger], function calls
- breakpoints, troubleshooting
- errors [debugger], finding which function call failed
- failures
- location breakpoint call failures
- errors [Visual Studio], function calls
- hit counts
- function calls, failure
- functions [debugger]
- Skip Count
ms.assetid: 66cfac86-f5be-4d3a-9329-d44cd74bc586
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 60e01816d6b123c95b8bab07189710869d0193f3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49180987"
---
# <a name="when-calling-a-function-hundreds-of-times-how-do-i-know-which-call-failed"></a>ある関数が何回も呼び出される場合、どの呼び出しでエラーが発生するのかを調べるには
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

問題の説明  
 `CnvtV` という関数を呼び出すとプログラムでエラーが発生します。 プログラムでエラーが発生するまでに、その関数は 200 回から 300 回は呼び出されているようです。 `CnvtV` に位置ブレークポイントを設定すると、この関数を呼び出すたびにプログラムが停止してしまうため、このブレークポイントは使用したくありません。 どのような条件で呼び出しが失敗するのかが不明なため、条件付きブレークポイントは設定できません。 どうしたらいいのでしょうか。  
  
## <a name="solution"></a>ソリューション  
 使用して、関数にブレークポイントを設定することができます、**ヒット カウント**フィールドの値の非常に高いため、絶対に到達することにします。 この場合、関数と思われるため、`CnvtV`いくつかが呼び出されます設定が数百回**ヒット カウント**に 1000 以上。 その後、プログラムを実行し、エラーが発生するのを待ちます。 エラーが発生したら、[ブレークポイント] ウィンドウを開き、ブレークポイントの一覧を確認します。 `CnvtV` に設定されたブレークポイントは、次のように、後ろにヒット カウントと残りの繰り返し回数が付いた状態で表示されます。  
  
```  
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)  
```  
  
 この関数は、101 回目の呼び出しで失敗したことがわかります。 ヒット カウントを 101 にしてブレークポイントを設定し直し、プログラムを再び実行します。すると、エラーの原因となった `CnvtV` 呼び出しのところでプログラムが停止します。  
  
## <a name="see-also"></a>関連項目  
 [ネイティブ コードのデバッグに関する Faq](../debugger/debugging-native-code-faqs.md)   
 [ブレークポイントの設定](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)



