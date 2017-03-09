---
title: "The folder &#39;folder&#39; could not be added to the project. &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.projfile_no_add_folder"
ms.assetid: 3f6a5aa7-17cc-4e78-93b7-96e0970e111e
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The folder &#39;folder&#39; could not be added to the project. &lt;reason&gt;
.vbproj ファイルまたは .csproj ファイルから読み取られたフォルダーをプロジェクトに追加できません。  原因は次のとおりです。  
  
-   名前が無効である。  
  
-   ファイルがパスに満たない。  たとえば、プロジェクトの相対パスとして "Folder1\\Folder2\\Folder3" があるときに、"Folder1\\Folder2" という相対パスのファイルも存在する場合があります。  
  
-   項目が既に存在している。  これは、フォルダーがプロジェクト ファイルに重複してリストされている場合に発生します。  
  
 このエラーの原因として最も可能性が高いのは、プロジェクト ファイルを手動で編集したことです。  
  
 **このエラーを解決するには**  
  
-   影響を受けたフォルダー ノードをプロジェクト ファイルから削除します。  
  
     この診断が表示されたフォルダー以下のすべてのフォルダーとファイルは、プロジェクトに追加されません。  
  
## 参照  
 [プロジェクト ファイル](/visual-cpp/ide/project-files)   
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/ja-jp/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)