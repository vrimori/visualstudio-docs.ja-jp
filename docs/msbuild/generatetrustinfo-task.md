---
title: "GenerateTrustInfo Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, GenerateTrustInfo task"
  - "GenerateTrustInfo task [MSBuild]"
ms.assetid: 3ca60816-4bb0-4fef-ae43-ca0bfb63def3
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# GenerateTrustInfo Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ベース マニフェスト、`TargetZone` パラメーター、および `ExcludedPermissions` パラメーターからアプリケーション信頼を生成します。  
  
## パラメーター  
 `GenerateTrustInfo` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|Description|  
|------------|-----------------|  
|`ApplicationDependencies`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。<br /><br /> 依存アセンブリを指定します。|  
|`BaseManifest`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem> 型のパラメーターです。<br /><br /> アプリケーション信頼の生成元のベース マニフェストを指定します。|  
|`ExcludedPermissions`|省略可能な `String` 型のパラメーターです。<br /><br /> ゾーンの既定のアクセス許可セットから除外される、セミコロン \(;\) で区切られた 1 つ以上のアクセス許可 ID 値を指定します。|  
|`TargetZone`|省略可能な `String` 型のパラメーターです。<br /><br /> コンピューター ポリシーから取得される、ゾーンの既定のアクセス許可セットを指定します。|  
|`TrustInfoFile`|必須の <xref:Microsoft.Build.Framework.ITaskItem> 型のパラメーターです。<br /><br /> アプリケーションのセキュリティ信頼情報を含むファイルを指定します。|  
  
## 解説  
 表に示されているパラメーターを使用できるだけでなく、このタスクは <xref:Microsoft.Build.Tasks.TaskExtension> クラスからパラメーターを継承します。このクラス自体は、<xref:Microsoft.Build.Utilities.Task> クラスから継承されます。  これらの追加のパラメーターの一覧とその説明については、「[TaskExtension Base Class](../msbuild/taskextension-base-class.md)」を参照してください。  
  
## 参照  
 [タスク](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)