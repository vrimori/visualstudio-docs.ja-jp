---
title: "引数に不正な値が渡された原因を見つけるには | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.parameters"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "デバッグ [C++], パラメーター"
  - "関数 [デバッガー], 検出 (無効なパラメーター値を)"
  - "パラメーター値, トラブルシューティング"
  - "パラメーター [デバッガー]"
  - "渡す (パラメーターを), トラブルシューティング (無効な値)"
ms.assetid: 1f1ae455-0e25-4e9d-b33f-53908f5bd6ce
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 引数に不正な値が渡された原因を見つけるには
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## 問題の説明  
 関数の 1 つに誤った引数値が渡されていることが判明しました。  この関数は頻繁に呼び出されます。  この関数に誤った値が渡されている場所を特定するにはどうしたらいいのでしょうか。  
  
## 解決方法  
  
#### この問題を解決するには  
  
1.  関数の先頭に位置ブレークポイントを設定します。  
  
2.  ブレークポイントを右クリックし、**\[条件\]** をクリックします。  
  
3.  **\[ブレークポイントの条件\]** ダイアログ ボックスで、**\[条件\]** チェック ボックスをオンにします。  「[高度なブレークポイント](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)」を参照してください。  
  
4.  テキスト ボックスに `Var==3` などの式を入力します \(`Var` は不適切な値が格納されるパラメーターの名前、`3` はこのパラメーターに渡される不適切な値\)。  
  
5.  **\[true の場合\]** オプション ボタンをクリックし、**\[OK\]** をクリックします。  
  
6.  そして、再びプログラムを実行します。  `Var` パラメーターの値が `3` になると、ブレークポイントによって、その関数の先頭でプログラムの実行が停止します。  
  
7.  次に、\[呼び出し履歴\] ウィンドウを使用して呼び出し元の関数を見つけ、その関数のソース コードに移動します。  詳細については、「[方法 : \[呼び出し履歴\] ウィンドウを使用する](../Topic/How%20to:%20Use%20the%20Call%20Stack%20Window.md)」を参照してください。  
  
## 参照  
 [ネイティブ コードのデバッグに関する FAQ](../debugger/debugging-native-code-faqs.md)   
 [Breakpoints](http://msdn.microsoft.com/ja-jp/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)