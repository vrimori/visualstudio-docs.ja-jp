---
title: "コマンド ラインの警告 D9042 | Microsoft Docs"
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
  - "D9042"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "D9042"
ms.assetid: d710693b-e422-40b2-b2dd-79e1b163b9e6
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# コマンド ラインの警告 D9042
'value' は '\/option' に対して無効な値です。'value' を仮定します。コード分析の警告は、このバージョンのコンパイラでは使用できません。  
  
 **\/wd**、**\/we**、**\/wo**、**\/wl** のいずれかのコマンド ライン オプションにコード分析の警告番号が追加され、コード分析をサポートしていないプラットフォームに **\/analyze** コマンド ライン オプションが指定されました。 この警告を解決するには、Visual Studio Team System の x86 バージョンに切り替えるか、**\/analyze** コマンド ライン オプションを削除します。  
  
## 使用例  
 次のコマンド ラインの例では、x64 システムまたは Itanium システムで警告 D9042 が生成されます。  
  
```  
cl /EHsc /LD /wd6001 /analyze filename.cpp  
```  
  
 この警告を解決するには、Visual Studio Team System の x86 バージョンに切り替え、**\/analyze** および **\/wd6001** の各コマンド ライン オプションを削除します。  
  
## 参照  
 [コマンド ライン エラー D8000 から D9999](/visual-cpp/error-messages/tool-errors/command-line-errors-d8000-through-d9999)   
 [コンパイラ オプション](/visual-cpp/build/reference/compiler-options)