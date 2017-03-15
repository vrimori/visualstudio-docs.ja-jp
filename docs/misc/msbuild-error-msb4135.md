---
title: "MSBuild エラー MSB4135 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSB4135"
ms.assetid: 9192f772-ad13-42f7-b53f-c5e31846fa5f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB4135
**MSB4135: レジストリの場所 "'\<key\>'" からツールセット情報を読み取り中にエラーが発生しました。'  \<key\>'**  
  
 レジストリに定義されたカスタム ツールセット情報を読み取ることができませんでした。  
  
### このエラーを解決するには  
  
-   カスタム ツールセットをレジストリに定義した場合は、その定義が有効なレジストリ形式であることを確認してください。正しい `ToolsVersion` 名と正しい `MSBuildBinPath` 値または `MSBuildToolsPath` 値が指定されている必要があります。  
  
## 参照  
 [標準ツールセット構成とカスタム ツールセット構成](../msbuild/standard-and-custom-toolset-configurations.md)   
 [Project Element \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [追加のリソース](../msbuild/additional-msbuild-resources.md)