---
title: "[値を変更できません] ダイアログ ボックス | Microsoft Docs"
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
  - "vs.debug.variables.failededit"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "[値を変更できません] ダイアログ ボックス"
  - "変数 [デバッガー]、編集"
ms.assetid: 19e930c2-5fbf-4c83-aae8-a1dc3f8fcae8
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# [値を変更できません] ダイアログ ボックス
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## エラー  
 `The value of this variable cannot be changed`  &#124; `The name` *name* `does not exist in the current context` &#124; *various other messages*  
  
 このメッセージ ボックスが表示されるのは、デバッガー ウィンドウ \(\[自動変数\]、\[ウォッチ\]、または \[ローカル\] の各ウィンドウ\)、または \[クイック ウォッチ\] ダイアログ ボックスで変数の内容を不正な値に変更しようとした場合です。  たとえば、整数値を文字列に設定しようとすると、このメッセージ ボックスが表示されます。  
  
## 解決方法  
 デバッグ用ウィンドウや \[クイック ウォッチ\] ダイアログ ボックスに入力した内容が、設定する変数に対して有効な値を表していることを確認します。  
  
## 参照  
 [デバッガー内の式](../debugger/expressions-in-the-debugger.md)