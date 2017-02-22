---
title: "ある関数が何回も呼び出される場合、どの呼び出しでエラーが発生するのかを調べるには | Microsoft Docs"
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
  - "vs.debug.functions"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "ブレークポイント, トラブルシューティング"
  - "条件付きブレークポイント"
  - "エラー [デバッガー], 検索 (失敗した関数呼び出しを)"
  - "エラー [デバッガー], 関数呼び出し"
  - "エラー [Visual Studio], 関数呼び出し"
  - "エラー"
  - "関数呼び出し, エラー"
  - "関数 [デバッガー]"
  - "ヒット カウント"
  - "位置ブレークポイントの呼び出し失敗"
  - "[Skip Count]"
ms.assetid: 66cfac86-f5be-4d3a-9329-d44cd74bc586
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# ある関数が何回も呼び出される場合、どの呼び出しでエラーが発生するのかを調べるには
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## 問題の説明  
 `CnvtV` という関数を呼び出すとプログラムでエラーが発生します。  プログラムでエラーが発生するまでに、その関数は 200 回から 300 回は呼び出されているようです。  `CnvtV` に位置ブレークポイントを設定すると、この関数を呼び出すたびにプログラムが停止してしまうため、このブレークポイントは使用したくありません。  どのような条件で呼び出しが失敗するのかが不明なため、条件付きブレークポイントは設定できません。  どうしたらいいのでしょうか。  
  
## 解決方法  
 **\[ヒット カウント\]** フィールドを使って、関数のブレークポイントに、絶対に到達不可能な大きい値を設定できます。  この場合、`CnvtV` 関数が 200 回から 300 回は呼び出されているようなので、**\[ヒット カウント\]** に 1000 以上の値を設定します。  その後、プログラムを実行し、エラーが発生するのを待ちます。  エラーが発生したら、\[ブレークポイント\] ウィンドウを開き、ブレークポイントの一覧を確認します。  `CnvtV` に設定されたブレークポイントは、次のように、後ろにヒット カウントと残りの繰り返し回数が付いた状態で表示されます。  
  
```  
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)  
```  
  
 この関数は、101 回目の呼び出しで失敗したことがわかります。  ヒット カウントを 101 にしてブレークポイントを設定し直し、プログラムを再び実行します。すると、エラーの原因となった `CnvtV` 呼び出しのところでプログラムが停止します。  
  
## 参照  
 [ネイティブ コードのデバッグに関する FAQ](../debugger/debugging-native-code-faqs.md)   
 [Setting Breakpoints](http://msdn.microsoft.com/ja-jp/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)