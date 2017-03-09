---
title: "Option Strict On では、&#39;&lt;modulename&gt;&#39; で定義された拡張メソッド &#39;&lt;extensionmethodname&gt;&#39; とデリゲート &#39;&lt;delegatename&gt;&#39; 間の暗黙的な型の縮小変換は許可されていません | Microsoft Docs"
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
  - "bc36709"
  - "vbc36709"
helpviewer_keywords: 
  - "BC36709"
ms.assetid: 95d8c833-3525-411b-98e8-b7d3f61f75c9
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On では、&#39;&lt;modulename&gt;&#39; で定義された拡張メソッド &#39;&lt;extensionmethodname&gt;&#39; とデリゲート &#39;&lt;delegatename&gt;&#39; 間の暗黙的な型の縮小変換は許可されていません
`Option Strict` がオンの場合、デリゲート内のパラメーターのデータ型から、そのデリゲート型の変数に割り当てられている拡張メソッドの対応するパラメーターへ縮小変換することはできません。 デリゲート パラメーターのデータ型は、拡張メソッドのデータ型に拡大変換する必要があります。  
  
 **エラー ID:** BC36709  
  
### このエラーを解決するには  
  
-   デリゲートまたは拡張メソッドのパラメーターのデータ型を変更して、必要な拡大関係が存在するようにします。  
  
## 参照  
 [拡張メソッド](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Relaxed Delegate Conversion](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [Delegates](/dotnet/visual-basic/programming-guide/language-features/delegates/delegates)   
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [ビルド内にありません: デリゲートと AddressOf 演算子](http://msdn.microsoft.com/ja-jp/7b2ed932-8598-4355-b2f7-5cedb23ee86f)