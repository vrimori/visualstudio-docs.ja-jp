---
title: "&lt;name&gt; is not a valid project name. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VS_E_INVALIDPROJECTNAME"
  - "vs.message.0x800A00D2"
ms.assetid: 2e8f3e58-f5f0-4f12-bae9-3acc58c0dca6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# &lt;name&gt; is not a valid project name.
このエラーが発生するのは一般的に、**\[コマンド\]** ウィンドウまたは **\[検索\]** ボックスから `File.NewProject` コマンドを発行する際、*projectname* に入力したプロジェクト名が正しくない場合です。  
  
### このエラーを解決するには  
  
1.  プロジェクト名に余分なスペースが含まれていないことや、プロジェクト名が NUL、CON、AUX などの予約語ではないことを確認します。  
  
     または  
  
     コマンドを入力し直し、プロジェクト名は省略します。  
  
## 参照  
 [コマンド ウィンドウ](../ide/reference/command-window.md)