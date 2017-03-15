---
title: "Error on line &lt;line&gt;. Expected &#39;expected&#39; but found &#39;found&#39; | Microsoft Docs"
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
  - "vs.tasklisterror.projfile_lineerr"
ms.assetid: d78934c9-6d57-42b2-9968-2b0aa4bf05e2
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error on line &lt;line&gt;. Expected &#39;expected&#39; but found &#39;found&#39;
これは、プロジェクト ファイルの読み取り時に発生する一般的な XML の解析エラーです。  このエラーは、ユーザーごとの設定ファイル \(.vbproj.user\/.csproj.user\) と同じように、プロジェクト ファイル \(.vbproj\/.csproj\) でも発生します。  プロジェクト システムによる詳細な情報は、パラメーター `expected` および `found` で確認できます。  
  
 このエラーは、多くの場合、プロジェクト \(ユーザー\) ファイルが編集されたことにより発生します。  
  
 **このエラーを解決するには**  
  
-   プロジェクト ファイルを再編集し、適切な状態に戻す必要があります。  
  
     エラーの重大度レベルによっては、このプロジェクトを開くことができなくなる場合もあります。  
  
## 参照  
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/ja-jp/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)