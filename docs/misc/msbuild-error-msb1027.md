---
title: "MSBuild エラー MSB1027 | Microsoft Docs"
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
  - "MSBuild.CannotAutoDisableAutoResponseFile"
helpviewer_keywords: 
  - "MSB1027"
ms.assetid: 2ef8d643-616c-4608-be76-5c2c8e18a9e7
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB1027
**\/noautoresponse スイッチは、MSBuild.rsp 自動応答ファイルにも、自動応答ファイルが参照する別の応答ファイルにも指定できません。**  
  
 **\/noautoresponse** スイッチが、MSBuild.rsp ファイル内、または MSBuild.rsp ファイルで指定されている別の応答ファイル内に見つかりました。  自動応答ファイルでそれ自体をオフにすることはできません。  
  
### このエラーを解決するには  
  
-   別の応答ファイルを指定します。  
  
-   **\/noautoresponse** スイッチを MSBuild.rsp 応答ファイルから削除します。  
  
## 参照  
 [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md)