---
title: "&#39;&lt;elementname&gt;&#39; はプロジェクト &#39;&lt;projectname&gt;&#39; の型 &#39;&lt;typename&gt;&#39; を参照していますが、型 &#39;&lt;typename&gt;&#39; がプロジェクト &#39;&lt;projectname&gt;&#39; にありません | Microsoft Docs"
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
  - "vbc30960"
  - "bc30960"
helpviewer_keywords: 
  - "BC30960"
ms.assetid: 4ed4bff5-c670-46f6-8360-7287444d50e5
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;elementname&gt;&#39; はプロジェクト &#39;&lt;projectname&gt;&#39; の型 &#39;&lt;typename&gt;&#39; を参照していますが、型 &#39;&lt;typename&gt;&#39; がプロジェクト &#39;&lt;projectname&gt;&#39; にありません
式は別のプロジェクトで参照されるクラス、構造体、モジュール、またはインターフェイスにアクセスしますが、そのプロジェクトに指定された型が含まれていません。  
  
 このエラーは、プロジェクトが同じソリューション内の別のプロジェクトへの間接参照を作成するときに発生します。 通常、プロジェクトは他のプロジェクトへの参照を作成するアセンブリへの参照を作成します。 アセンブリが他のプロジェクトの指定された型にアクセスする場合、その型への間接参照が確立されます。 しかし、他のプロジェクトに指定された型が存在しない場合は、このエラーが生成されます。  
  
 **エラー ID:** BC30960  
  
### このエラーを解決するには  
  
-   当該の型がどこにも定義されなくなった場合は、その型にアクセスしようとするステートメントを削除するか、置き換えます。 また、当該の型への間接参照を提供するアセンブリでも、同じ変更が必要になる場合があります。  
  
-   当該の型がどこかに定義されている場合は、それを定義するプロジェクトまたはアセンブリへの直接参照を作成します。  
  
## 参照  
 [NIB: 名前空間およびコンポーネントの参照](http://msdn.microsoft.com/ja-jp/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [プロジェクト内の参照の管理](../ide/managing-references-in-a-project.md)   
 [NIB: 参照の管理](http://msdn.microsoft.com/ja-jp/910912ce-0dc9-4569-9274-32c44a20cb2c)   
 [NIB 方法: &#91;参照の追加&#93; ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/ja-jp/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)