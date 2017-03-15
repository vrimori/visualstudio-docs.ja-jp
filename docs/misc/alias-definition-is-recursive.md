---
title: "Alias definition is recursive. | Microsoft Docs"
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
  - "vs.message.0x800A00DA"
  - "vs.message.VS_E_RECURSIVEALIAS"
ms.assetid: e48a2908-9b94-4c6a-9807-beeeba71531c
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Alias definition is recursive.
このエラーが発生するのは一般的に、エイリアスが直接的または間接的にそれ自身を参照するように定義されている場合です。  
  
### このエラーを解決するには  
  
1.  エイリアスの定義を変更してやり直します。  
  
     または  
  
2.  \[コマンド\] ウィンドウに「`>alias`」と入力して、エイリアスとその定義の現在の一覧を再確認し、やり直します。  
  
## 参照  
 [Alias コマンド](../ide/reference/alias-command.md)   
 [Visual Studio コマンドの定義済みのエイリアス](../ide/reference/visual-studio-command-aliases.md)