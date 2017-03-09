---
title: "The project file &#39;&lt;filename&gt;&#39; cannot be updated | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.UpgradeErrors"
ms.assetid: ecd1e161-c51c-4aaa-ab80-8fc443bdad81
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The project file &#39;&lt;filename&gt;&#39; cannot be updated
旧バージョンの [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] で作成したプロジェクトを開こうとしています。  プロジェクトを現在の形式に更新する必要がありますが、更新できません。指定されたプロジェクト ファイル \(.vbproj\) が読み取り専用であるか、またはファイルがソース コード管理下にあり、別のユーザーによって現在ロックされているためです。  
  
### このエラーを解決するには  
  
1.  ファイル エクスプローラーで、指定されたプロジェクト ファイルを検索します。  
  
2.  **\[ファイル\]** メニューの **\[プロパティ\]** をクリックします。  
  
3.  **\[プロパティ\]** ダイアログ ボックスで、**\[読み取り専用\]** 属性をオフにします。  
  
 ファイルがソース コード管理下にあり、別のユーザーによってロックされている場合は、ファイルが使用可能になるまで待機してから、ローカルでチェックアウトしてください。  
  
## 参照  
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/ja-jp/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)