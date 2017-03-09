---
title: "MSBuild エラー MSB1002 | Microsoft Docs"
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
  - "MSBuild.UnexpectedParametersError"
helpviewer_keywords: 
  - "MSB1002"
ms.assetid: 798c9690-6d99-4f21-a491-ab44d3f3c552
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB1002
**このスイッチにはパラメーターを指定できません。**  
  
 このスイッチではパラメーターを定義することはできません。  スイッチの名前だけを指定してください。後ろにコロンを指定することはできません。  
  
### このエラーを解決するには  
  
-   このスイッチでは、パラメーターを付けずにコマンドを入力します。「`msbuild /<switch>:<parameters>`」ではなく、「`msbuild /<switch>`」のように入力します。  
  
-   スイッチ名の後のコロンを削除します。「`msbuild /<switch>:`」ではなく、「`msbuild /<switch>`」のように入力します。  
  
## 参照  
 [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md)