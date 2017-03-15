---
title: "アセンブリ &#39;&lt;assemblyname&gt;&#39; の型 &#39;&lt;typename&gt;&#39; はそれ自体に転送され、サポートされていない型もそれ自体に転送されました | Microsoft Docs"
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
  - "bc31425"
  - "vbc31425"
helpviewer_keywords: 
  - "BC31425"
  - "型の転送"
ms.assetid: e3275d55-3f4c-4bbc-9c8f-f55c4e973063
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# アセンブリ &#39;&lt;assemblyname&gt;&#39; の型 &#39;&lt;typename&gt;&#39; はそれ自体に転送され、サポートされていない型もそれ自体に転送されました
アセンブリがそれ自体の型を別のアセンブリに転送するために <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> を使用していますが、同じアセンブリの同じ型を指定しています。  
  
 *型の転送*とは、最初に定義されたもの以外のアセンブリにクラス、構造体、インターフェイス、デリゲート、または列挙体の定義を再割り当てすることを意味します。 これは*コードのリファクタリング*と組み合わせてよく使用され、これにより、1 つのアセンブリを 2 つ以上のアセンブリに分割したり、アセンブリ間でコードを移動したりできます。  
  
 それ自体に型を転送すると、結果として循環転送になります。 転送された型に別のアセンブリがアクセスしようとすると、転送されていない型には到達できないため、無限に転送が続きます。  
  
 **エラー ID:** BC31425  
  
### このエラーを解決するには  
  
-   対象の型を別のアセンブリ内の型に転送するか、一切転送を行わないでください。  
  
## 参照  
 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>   
 [Type Forwarding \(C\+\+\/CLI\)](/visual-cpp/windows/type-forwarding-cpp-cli)   
 [プロジェクト内の参照の管理](../ide/managing-references-in-a-project.md)   
 [NIB 方法: &#91;参照の追加&#93; ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/ja-jp/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)