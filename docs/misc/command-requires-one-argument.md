---
title: "Command requires one argument. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VS_E_INCORRECTPARAMCOUNT1"
  - "vs.message.0x800A00C3"
ms.assetid: b4d98e6d-6970-42fb-b1de-43f2e952fb9d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Command requires one argument.
このエラーが発生するのは一般的に、コマンドに入力された情報が不十分な場合、または引数の組み合わせが正しくない場合です。  
  
 たとえば、`alias` コマンドを「`alias` `/delete sample1 sample2`」と入力した場合、エイリアス `/delete` は 1 つのエイリアスしかとれないために、このエラーが表示されます。  エイリアス名はスペースを含まないので、\[検索\] ボックスと \[コマンド\] ウィンドウは `sample1 sample2` を 2 つの異なるエイリアス名として解釈します。  
  
### このエラーを解決するには  
  
1.  ドキュメントでコマンドの正しい構文を確認して、やり直します。  
  
## 参照  
 [Visual Studio コマンド](../ide/reference/visual-studio-commands.md)