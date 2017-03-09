---
title: "コンパイラ エラー CS1944 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1944"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1944"
ms.assetid: e5e2c018-9a7e-48ee-8dd3-98e3553777c1
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1944
式ツリーは、アンセーフ ポインター操作を含むことはできません  
  
 <xref:System.Linq.Expressions.Expression%601.Compile%2A?displayProperty=fullName> メソッドは検証可能なコードの作成のみが許可されているため、式ツリーはポインター型をサポートしません。 コメントを参照してください。  
  
### このエラーを解決するには  
  
1.  式ツリーを作成するときに、ポインター型を使用しないようにします。  
  
## 使用例  
 次の例では、CS1944 が生成されます。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 状況によっては、式ツリーでポインターを使用できることがあります。 次に例を示します。  
  
 `Expression<Func\<int*[], int*[]>) e = (int*[] i)=>i;`  
  
 このコードは、いずれの型引数もポインター型ではないため、有効な式ツリーです。 これらはポインターの配列で、配列はポインター型ではありません。 また、式ツリーの本体では、いずれのポインターも正常に機能します。  
  
## 参照  
 [安全でない](/dotnet/csharp/language-reference/keywords/unsafe)