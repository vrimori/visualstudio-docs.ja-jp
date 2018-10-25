---
title: 引数に不正な値が渡された原因を見つけるには | Microsoft Docs
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
- vs.debug.parameters
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], parameters
- parameters [debugger]
- passing parameters, troubleshooting wrong values
- functions [debugger], detecting wrong parameter values
- parameter values, troubleshooting
ms.assetid: 1f1ae455-0e25-4e9d-b33f-53908f5bd6ce
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87d44eeabd3c65d6d86125c4029bfc868a539f8c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49207624"
---
# <a name="how-can-i-find-out-who-is-passing-a-wrong-parameter-value"></a>引数に不正な値が渡された原因を見つけるには
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

問題の説明  
 関数の 1 つに誤った引数値が渡されていることが判明しました。 この関数は頻繁に呼び出されます。 この関数に誤った値が渡されている場所を特定するにはどうしたらいいのでしょうか。  
  
## <a name="solution"></a>ソリューション  
  
#### <a name="to-resolve-this-problem"></a>この問題を解決するには  
  
1.  関数の先頭に位置ブレークポイントを設定します。  
  
2.  ブレークポイントを右クリックして**条件**します。  
  
3.  **ブレークポイント条件**ダイアログ ボックスをクリックして、**条件**チェック ボックスをオンします。 参照してください[ブレークポイントの高度な](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)します。  
  
4.  テキスト ボックスに `Var==3` などの式を入力します (`Var` は不適切な値が格納されるパラメーターの名前、`3` はこのパラメーターに渡される不適切な値)。  
  
5.  選択、 **true**ボタンをクリックし、をクリックして、 **OK**ボタン。  
  
6.  そして、再びプログラムを実行します。 `Var` パラメーターの値が `3` になると、ブレークポイントによって、その関数の先頭でプログラムの実行が停止します。  
  
7.  次に、[呼び出し履歴] ウィンドウを使用して呼び出し元の関数を見つけ、その関数のソース コードに移動します。 詳細については、次を参照してください。[方法: 呼び出し履歴 ウィンドウを使用して、](../debugger/how-to-use-the-call-stack-window.md)します。  
  
## <a name="see-also"></a>関連項目  
 [ネイティブ コードのデバッグに関する Faq](../debugger/debugging-native-code-faqs.md)   
 [ブレークポイント](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)



