---
title: "基本メソッドになる &#39;&lt;method2&gt;&#39; のアクセスを拡張するので、&#39;&lt;method1&gt;&#39; はオーバーライドを行えません | Microsoft Docs"
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
  - "vbc32203"
  - "bc32203"
helpviewer_keywords: 
  - "BC32203"
ms.assetid: ef7816a4-5f57-4346-80fc-9311bc150b6b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 基本メソッドになる &#39;&lt;method2&gt;&#39; のアクセスを拡張するので、&#39;&lt;method1&gt;&#39; はオーバーライドを行えません
プロシージャで `Overrides` が指定されていますが、宣言されているアクセシビリティによる制限が、オーバーライドされるメソッドのアクセシビリティの制限よりも緩く設定されています。 アクセシビリティを拡張することはできません。つまり、オーバーライドするメソッドを、オーバーライドされるメソッドよりもアクセスしやすくすることはできません。 たとえば、基底クラスのメソッドが `Protected` である場合は、この基底クラスのメソッドを `Public` のメソッドでオーバーライドできません。  
  
 **エラー ID:** BC32203  
  
### このエラーを解決するには  
  
-   `Overrides` キーワードを削除するか、少なくとも基底クラスのメソッドと同じ制限になるようにアクセシビリティを変更します。  
  
## 参照  
 [ビルド内にありません: プロパティとメソッドのオーバーライド](http://msdn.microsoft.com/ja-jp/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [Access Levels in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)   
 [Shadowing in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/shadowing)