---
title: "At least one folder is missing the &#39;attribute&#39; attribute | Microsoft Docs"
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
  - "vs.tasklisterror.projfile_missing_fold_attrib"
ms.assetid: 3a0498a9-df61-47d8-a228-f88f4f138df8
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# At least one folder is missing the &#39;attribute&#39; attribute
.vbproj ファイルまたは .csproj ファイルから読み取られたフォルダー ノードに、プロジェクト システムによって必要とされる特定の属性が欠落しています。  現在これに当てはまる属性は、**RelPath** 属性だけです。この属性は、プロジェクト フォルダー下で特定のフォルダーが格納される場所を指定します。  
  
 このエラーの原因として最も可能性が高いのは、プロジェクト ファイルを手動で編集したことです。  
  
 **このエラーを解決するには**  
  
-   影響を受けたフォルダー ノードをプロジェクト ファイルから削除します。  このフォルダーがまだディスク上に存在する場合は、すべてのファイルを表示モードに切り替え \(ソリューション エクスプローラーのツール バーにある \[すべてのファイルを表示\] ボタンをクリック\)、影響を受けたフォルダーを右クリックし、**\[プロジェクトに含める\]** をクリックします。  
  
     属性が欠落しているフォルダーは、プロジェクトに追加されません。  
  
## 参照  
 [プロジェクト ファイル](/visual-cpp/ide/project-files)   
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/ja-jp/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)