---
title: "コンパイラによって検出された &#39;System.Runtime.CompilerServices.ExtensionAttribute&#39; のカスタム設計されたバージョンが無効です | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36558"
  - "bc36558"
helpviewer_keywords: 
  - "BC36558"
ms.assetid: f47d310a-95fd-4340-bda2-21262c217dbb
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# コンパイラによって検出された &#39;System.Runtime.CompilerServices.ExtensionAttribute&#39; のカスタム設計されたバージョンが無効です
コンパイラによって検出された 'System.Runtime.CompilerServices.ExtensionAttribute' のカスタム設計されたバージョンが無効です。 その属性の使用フラグは、アセンブリ、クラス、およびメソッドを許可するように設定する必要があります。  
  
 コンパイラによって検出された <xref:System.Runtime.CompilerServices.ExtensionAttribute?displayProperty=fullName> のカスタム設計バージョンは、アセンブリ、メソッド、およびクラスへの属性の適用を有効にするように、属性使用フラグを設定していません。 少なくともこれら 3 つのプログラム要素への適用が必要です。  
  
 **エラー ID:** BC36558  
  
### このエラーを解決するには  
  
-   次の例に示すように、少なくともアセンブリ、メソッド、およびクラスに属性を適用できるように、属性の定義を変更します。  
  
-   カスタム設計バージョンの代わりに <xref:System.Runtime.CompilerServices.ExtensionAttribute?displayProperty=fullName> を使用します。  
  
## 使用例  
 次の例では、`AttributeUsage` 属性を使用して、`ExtensionAttribute` の新しいバージョンがどのプログラム要素に適用可能かを指定します。 この例では、`AttributeTargets` 列挙体の 3 つのメンバーである `Assembly`、`Class`、`Method` を指定します。 これらの要素のいずれかがないと、このエラーが発生します。  
  
```  
Namespace System.Runtime.CompilerServices <AttributeUsage(AttributeTargets.Assembly Or _ AttributeTargets.Class Or AttributeTargets.Method)> Class ExtensionAttribute Inherits System.Attribute ' Definitions of methods, fields, and properties. End Class End Namespace  
```  
  
 あるいは、`AttributeTargets` の `All` メンバーを使用して、`ExtensionAttribute` をすべてのプログラム要素に適用可能にすることもできます。  
  
```  
<AttributeUsage(AttributeTargets.All)>  
```  
  
 次のコードに示すように、`AttributeUsage` の行を削除すると同じ結果が生じます。  
  
```  
Namespace System.Runtime.CompilerServices Class ExtensionAttribute Inherits System.Attribute ' Definitions of methods, fields, and properties. End Class End Namespace  
```  
  
## 参照  
 <xref:System.Runtime.CompilerServices.ExtensionAttribute>   
 [ビルド内にありません: Visual Basic での属性の概要](http://msdn.microsoft.com/ja-jp/0d0cff64-892d-4f57-83bd-bef388553d4f)   
 [ビルド内にありません: Visual Basic におけるカスタム属性](http://msdn.microsoft.com/ja-jp/d72d8a5c-8f64-4614-b15b-cad66845d047)   
 [拡張メソッド](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [ビルド内にありません: 方法: 独自の属性を定義する](http://msdn.microsoft.com/ja-jp/039609c4-ec43-4f44-945f-aa3b5b535c6a)   
 [カスタム属性の記述](../Topic/Writing%20Custom%20Attributes.md)