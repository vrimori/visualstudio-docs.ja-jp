---
title: "MSBuild エラー MSB3021 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.Copy.Error"
helpviewer_keywords: 
  - "MSB3021"
ms.assetid: 8cb3a860-6916-4406-b5c7-b1106b44b92a
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3021
**ファイル "\<ファイル\>" をファイル "\<ファイル\>" にコピーできません。'  \<エラー\>'**  
  
 `Copy` タスクが、指定されたファイルをコピーできません。  
  
### このエラーを解決するには  
  
-   コピー先のファイルが別のアプリケーションによってロックされていないか \(使用中でないか\) どうかを確認します。  ソース ファイルを読み取るため、およびコピー先のファイルをコピー先のフォルダーに書き込むためのアクセス許可があることを確認します。  出力先ファイルのパスが非常に長い場合、別の場所にコピーする必要があります。  
  
## 参照  
 [Copy Task](../msbuild/copy-task.md)   
 [タスク](../msbuild/msbuild-tasks.md)