---
title: "MSBuild Response Files | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
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
  - "response files, MSBuild"
  - "MSBuild, response files"
  - "MSBuild, .rsp files"
  - ".rsp files"
ms.assetid: 9f53987b-20ee-470a-ab62-fce997bb5e15
caps.latest.revision: 3
caps.handback.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild Response Files
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

応答 \(.rsp\) ファイルは、MSBuild.exe のコマンド ライン スイッチを含むテキスト ファイルです。  各スイッチを個別の行に記述することも、すべてのスイッチを 1 つの行に記述することもできます。  コメント行は、**\#** 記号で始まります。  **@** スイッチは、MSBuild.exe に別の応答ファイルを渡すために使用されます。  
  
 自動応答ファイルは、プロジェクトをビルドする際に MSBuild.exe が自動的に使用する特別な .rsp ファイルです。  この MSBuild.rsp ファイルは、MSBuild.exe と同じディレクトリに配置しないと検出されません。  このファイルを編集して、MSBuild.exe に既定のコマンド ライン スイッチを指定できます。  たとえば、プロジェクトをビルドする際に毎回同じ logger を使用する場合は、**\/logger** スイッチを MSBuild.rsp に追加することで、プロジェクトがビルドされるたびに MSBuild.exe がその logger を使用するようになります。  
  
## 参照  
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md)