---
title: "VCMessage Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.task.vcmessage"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "VCMessage task (MSBuild (Visual C++))"
  - "MSBuild (Visual C++), VCMessage task"
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# VCMessage Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ビルド時の警告メッセージおよびエラー メッセージをログに記録します。  
  
## 解説  
 このタスクは Visual C\+\+ の MSBuild の実装を支援します。ユーザーが呼び出すためのものではありません。  詳細については、「<xref:Microsoft.Build.Utilities.TaskLoggingHelper>」を参照してください。  
  
## パラメーター  
 **VCMessage** タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|Description|  
|------------|-----------------|  
|**Arguments**|省略可能な **String** 型のパラメーターです。<br /><br /> 表示するメッセージのセミコロン区切りのリストです。|  
|**Code**|必須の **String** 型のパラメーターです。<br /><br /> メッセージに付けるエラー番号です。|  
|**Type**|省略可能な **String** 型のパラメーターです。<br /><br /> 出力するメッセージの種類を指定します。  警告メッセージを出力する場合は `"Warning"` を指定し、エラー メッセージを出力する場合は `"Error"` を指定します。|  
  
## 参照  
 [Task Reference](../msbuild/msbuild-task-reference.md)