---
title: 引数に不正な値が渡された原因を見つけるには | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.parameters
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], parameters
- parameters [debugger]
- passing parameters, troubleshooting wrong values
- functions [debugger], detecting wrong parameter values
- parameter values, troubleshooting
ms.assetid: 1f1ae455-0e25-4e9d-b33f-53908f5bd6ce
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7c2f73f94695d43cea29c3f23b1c3a0c74e79f01
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-can-i-find-out-who-is-passing-a-wrong-parameter-value"></a>引数に不正な値が渡された原因を見つけるには
## <a name="problem-description"></a>問題の説明  
 関数の 1 つに誤った引数値が渡されていることが判明しました。 この関数は頻繁に呼び出されます。 この関数に誤った値が渡されている場所を特定するにはどうしたらいいのでしょうか。  
  
## <a name="solution"></a>ソリューション  
  
#### <a name="to-resolve-this-problem"></a>この問題を解決するには  
  
1.  関数の先頭に位置ブレークポイントを設定します。  
  
2.  ブレークポイントを右クリックし **条件**です。  
  
3.  **ブレークポイント条件**ダイアログ ボックスをクリックして、**条件**チェック ボックスをオンします。 参照してください[ブレークポイントを高度な](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)します。  
  
4.  テキスト ボックスに `Var==3` などの式を入力します (`Var` は不適切な値が格納されるパラメーターの名前、`3` はこのパラメーターに渡される不適切な値)。  
  
5.  選択、 **true**ラジオ ボタン、およびをクリックして、 **OK**ボタンをクリックします。  
  
6.  そして、再びプログラムを実行します。 `Var` パラメーターの値が `3` になると、ブレークポイントによって、その関数の先頭でプログラムの実行が停止します。  
  
7.  次に、[呼び出し履歴] ウィンドウを使用して呼び出し元の関数を見つけ、その関数のソース コードに移動します。 詳細については、次を参照してください。[する方法: 呼び出し履歴 ウィンドウを使用して](../debugger/how-to-use-the-call-stack-window.md)です。  
  
## <a name="see-also"></a>関連項目  
 [ネイティブ コードのデバッグに関する Faq](../debugger/debugging-native-code-faqs.md)   
 [ブレークポイント](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)