---
title: "プロジェクト &#39;&lt;projectname1&gt;&#39; は、&#39;&lt;typename&gt;&#39; を含むプロジェクト &#39;&lt;projectname2&gt;&#39; を間接的に参照しています | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31532"
  - "bc31532"
helpviewer_keywords: 
  - "BC31532"
ms.assetid: 9ef6574e-b049-4a2e-9b12-fea2dfe06cd1
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# プロジェクト &#39;&lt;projectname1&gt;&#39; は、&#39;&lt;typename&gt;&#39; を含むプロジェクト &#39;&lt;projectname2&gt;&#39; を間接的に参照しています
プロジェクト '\<projectname1\>' は、'\<typename\>' を含むプロジェクト '\<projectname2\>' を間接的に参照しています。 プロジェクトに '\<projectname2\>' へのプロジェクト参照を追加します。  
  
 プロジェクト内のコードでは、別のプロジェクトで定義されている型にアクセスしますが、定義しているプロジェクトへの直接参照がプロジェクトにありません。  
  
 型は、クラス、構造体、インターフェイス、または列挙型になります。  
  
 表示されている型を定義するプロジェクトでは、その型を含むアセンブリを生成します。 プロジェクトが定義しているプロジェクトを直接参照しない場合、コンパイラでは、型を含むアセンブリがソリューション内にあり、アクセス可能であることを保証できません。  
  
 **エラー ID:** BC31532  
  
### このエラーを解決するには  
  
-   表示されている型を定義しているプロジェクトを特定し、それに対するプロジェクト参照を追加します。  
  
## 参照  
 [NIB: 名前空間およびコンポーネントの参照](http://msdn.microsoft.com/ja-jp/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [プロジェクト内の参照の管理](../ide/managing-references-in-a-project.md)   
 [NIB: 参照の管理](http://msdn.microsoft.com/ja-jp/910912ce-0dc9-4569-9274-32c44a20cb2c)   
 [NIB 方法: &#91;参照の追加&#93; ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/ja-jp/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)