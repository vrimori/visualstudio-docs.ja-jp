---
title: "&#39;Microsoft.VisualBasic.ComClassAttribute&#39; がクラス &#39;&lt;classname&gt;&#39; に対して指定されていますが、そのクラスには COM に公開できるパブリック メンバーが含まれていないため、COM インターフェイスは生成されません | Microsoft Docs"
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
  - "bc40011"
  - "vbc40011"
helpviewer_keywords: 
  - "BC40011"
ms.assetid: 39aed273-bf27-4667-8116-022c4dd8f3c5
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Microsoft.VisualBasic.ComClassAttribute&#39; がクラス &#39;&lt;classname&gt;&#39; に対して指定されていますが、そのクラスには COM に公開できるパブリック メンバーが含まれていないため、COM インターフェイスは生成されません
`COMClassAttribute` 属性ブロックを使用するクラスで、`Public` プロパティまたはメソッドが定義されていません。 クラスを COM オブジェクトとして公開する場合は、そのプロパティとメソッドを `Public` アクセスで宣言する必要があります。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
 **エラー ID:** BC40011  
  
### このエラーを解決するには  
  
-   `Public` キーワードをクラス内の 1 つ以上のプロパティまたはメソッドに追加するか、`COMClassAttribute` 属性ブロックを削除します。  
  
## 参照  
 [ビルド内にありません: Visual Basic で使用される属性](http://msdn.microsoft.com/ja-jp/22231318-8a40-49af-9245-e0aab723563b)   
 [ビルド内にありません: 属性の適用](http://msdn.microsoft.com/ja-jp/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Public](/dotnet/visual-basic/language-reference/modifiers/public)   
 [ComClassAttribute クラス](http://msdn.microsoft.com/ja-jp/5c2f0835-9210-47dc-bc59-5c1769953574)