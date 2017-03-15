---
title: "SetEnv Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.task.setenv"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "MSBuild (Visual C++), tasks"
  - "SetEnv task (MSBuild (Visual C++))"
ms.assetid: fd9e4225-68cb-4608-8b27-468b0218c936
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# SetEnv Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定された環境変数の値を設定または削除します。  
  
## パラメーター  
 **SetEnv** タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|Description|  
|------------|-----------------|  
|**Name**|必須の **String** 型のパラメーターです。<br /><br /> 環境変数の名前。|  
|**OutputEnvironmentVariable**|省略可能な **String** 型の出力パラメーターです。<br /><br /> **Name** パラメーターで指定されている環境変数に割り当てる値を格納します。|  
|**Prefix**|必須の `Boolean` 型のパラメーターです。<br /><br /> `true` の場合、**Name** パラメーターで指定されている環境変数の値の前に **Value** パラメーターの値を連結し、その結果を環境変数に割り当てます。  `false` の場合は、**Value** パラメーターの値だけを環境変数に割り当てます。|  
|**Target**|省略可能な **String** 型のパラメーターです。<br /><br /> 環境変数の格納場所を指定します。  "`User`" または "`Machine`" を指定します。<br /><br /> 詳細については、[MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web サイトの「EnvironmentVariableTarget 列挙体」を参照してください。|  
|**Value**|省略可能な **String** 型のパラメーターです。<br /><br /> **Name** パラメーターで指定されている環境変数に割り当てる値。  **Value** が空で、変数が存在する場合、その変数は削除されます。  変数が存在せず、操作を実行できなかったとしても、エラーは発生しません。<br /><br /> 詳細については、[MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web サイトの「Environment::SetEnvironmentVariable メソッド」を参照してください。|  
  
## 解説  
  
## 参照  
 [Task Reference](../msbuild/msbuild-task-reference.md)