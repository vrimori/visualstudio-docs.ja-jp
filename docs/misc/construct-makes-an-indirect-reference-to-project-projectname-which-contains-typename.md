---
title: "コンストラクトは、&#39;&lt;typename&gt;&#39; を含むプロジェクト &#39;&lt;projectname&gt;&#39; を間接的に参照しています | Microsoft Docs"
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
  - "vbc31533"
  - "bc31533"
helpviewer_keywords: 
  - "BC31533"
ms.assetid: e3f55f9f-92be-4ecb-bc8f-9e57049a0805
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# コンストラクトは、&#39;&lt;typename&gt;&#39; を含むプロジェクト &#39;&lt;projectname&gt;&#39; を間接的に参照しています
コンストラクトは、'\<typename\>' を含むプロジェクト '\<projectname\>' を間接的に参照しています。 プロジェクトに '\<projectname\>' へのプロジェクト参照を追加します。  
  
 式またはステートメントが、別のプロジェクトで定義されている型にアクセスしますが、ご使用のプロジェクトには定義している側のプロジェクトへの直接的な参照がありません。  
  
 型は、クラス、構造体、インターフェイス、モジュール、または列挙型になります。  
  
 言及されている型を定義するプロジェクトでは、その型を含むアセンブリを生成します。 定義している側のプロジェクトがご使用のプロジェクトによって直接的に参照されていない場合、コンパイラは、型を含むアセンブリがソリューション内にあること、およびそれにアクセスできることを保証できません。  
  
 **エラー ID:** BC31533  
  
### このエラーを解決するには  
  
-   言及されている型を定義しているプロジェクトを特定し、それに対するプロジェクト参照を追加します。  
  
## 参照  
 [NIB: 名前空間およびコンポーネントの参照](http://msdn.microsoft.com/ja-jp/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [プロジェクト内の参照の管理](../ide/managing-references-in-a-project.md)   
 [NIB: 参照の管理](http://msdn.microsoft.com/ja-jp/910912ce-0dc9-4569-9274-32c44a20cb2c)   
 [NIB 方法: &#91;参照の追加&#93; ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/ja-jp/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)