---
title: "Error copying the application configuration file to the run directory. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cant_copy_appcfg_file"
ms.assetid: 15699a76-16ef-40a8-8ed4-5eef4d2c0e72
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error copying the application configuration file to the run directory. &lt;reason&gt;
プロジェクト システムが、プロジェクトの実行場所のディレクトリから app.config をコピーできませんでした。  このエラーが発生した場合、ビルド プロセスは失敗します。  
  
 このエラーは、実行可能ファイル \(.exe\) の作成時に発生します。  
  
 ビルド システムは、プロジェクトのルート フォルダーで **app.config** と呼ばれるファイルを検索します。  このファイルは、プロジェクトの出力ディレクトリに *outputfile.*config という名前でコピーされます。  
  
 エラーの原因には次のことが考えられます。  
  
-   ディスク容量が不足している。  
  
-   MAX\_PATH を超えている。  
  
 実行中のアプリケーションのコピーがほかに存在しないことを確認する必要もあります。  
  
## 参照  
 [NIB How to: Modify Project Properties and Configuration Settings](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)