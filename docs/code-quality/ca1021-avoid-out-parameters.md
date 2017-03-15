---
title: "CA1021: out パラメーターを使用しません | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1021"
  - "AvoidOutParameters"
helpviewer_keywords: 
  - "AvoidOutParameters"
  - "CA1021"
ms.assetid: 970f2304-842c-4fb7-9734-f3871da8d479
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA1021: out パラメーターを使用しません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidOutParameters|  
|CheckId|CA1021|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## 原因  
 パブリック型のパブリック メソッドまたはプロテクト メソッドに `out` パラメーターが含まれます。  
  
## 規則の説明  
 \(`out` または `ref` を使用した\) 型の参照渡しには、ポインターの使用経験、値型と参照型の違いの理解、および複数の戻り値を持つメソッドの処理が必要です。  また、`out` パラメーターと `ref` パラメーターの違いがあまり理解されていません。  
  
 参照型の "参照" 渡しの場合、メソッドは、オブジェクトの別のインスタンスを返すパラメーターを使用しようとします。  参照型の参照渡しは、ダブル ポインターの使用、ポインターへのポインター、または二重の間接参照とも呼ばれます。  既定の呼び出し規約では、"値" 渡しですが、参照型を使用するパラメーターは、既にオブジェクトに対するポインターを受け取っています。  ポインター \(指し示す先のオブジェクトではなく\) は、値渡しです。  値渡しとは、メソッドで、ポインターの指し示す先を新しいインスタンスの参照型に変更できないということです。  ただし、ポインターの指し示すオブジェクトの内容を変更することはできます。  ほとんどのアプリケーションは値渡しで十分で、目的の動作を実現できます。  
  
 メソッドで異なるインスタンスを返す必要がある場合、メソッドの戻り値を使用して実現します。  文字列を操作するさまざまなメソッドの <xref:System.String?displayProperty=fullName> クラスを参照して、文字列の新しいインスタンスを返します。  このモデルを使用する場合、呼び出し元は、元のオブジェクトが保存されているかどうかを判断する必要があります。  
  
 戻り値は一般的であり、よく使用されますが、`out` パラメーターと `ref` パラメーターを適切に使用する場合、中間のデザインとコーディング技術が必要です。  開発者全般に向けてライブラリをデザインする場合、ユーザーが `out` パラメーターまたは `ref` パラメーターの扱い方を習得することは期待しないでください。  
  
## 違反の修正方法  
 値型によって発生したこの規則違反を修正するには、メソッドからオブジェクトを戻り値として返すようにします。  メソッドで複数の値を返す必要がある場合、値を保持しているオブジェクトの 1 インスタンスを返すようにメソッドをデザインし直します。  
  
 参照型によって発生したこの規則違反を修正するには、参照の新しいインスタンスを返すようにします。  この場合、メソッドで戻り値を使用して実行します。  
  
## 警告を抑制する状況  
 この規則による警告を抑制しても安全です。  ただし、このデザインのままでは操作性の問題が発生する可能性があります。  
  
## 使用例  
 次のライブラリで、ユーザーのフィードバックに対して応答を生成するクラスの実装例を 2 つ示します。  最初の実装 \(`BadRefAndOut`\) によって、ライブラリ ユーザーは 3 つの戻り値を管理することになります。  2 つ目の実装 \(`RedesignedRefAndOut`\) は、ユーザー エクスペリエンスをわかりやすいものにします。これは、データを単体のユニットとして管理するコンテナー クラスのインスタンス \(`ReplyData`\) を返すことで実現しています。  
  
 [!code-cs[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_1.cs)]  
  
## 使用例  
 次のアプリケーションは、ユーザー エクスペリエンスを説明した例です。  再デザインしたライブラリの呼び出し \(`UseTheSimplifiedClass`メソッド\) はわかりやすく、このメソッドで返される情報は管理が容易です。  2 つのメソッドの出力結果は同じです。  
  
 [!code-cs[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_2.cs)]  
  
## 使用例  
 次のライブラリ例は、参照型の `ref` パラメーターの使用方法を示します。また、この機能の実装方法を改善しています。  
  
 [!code-cs[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_3.cs)]  
  
## 使用例  
 次のアプリケーションでは、ライブラリの各メソッドの動作を説明するために、それぞれを呼び出しています。  
  
 [!code-cs[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_4.cs)]  
  
 この例を実行すると、次の出力が生成されます。  
  
  **Changing pointer \- passed by value:**  
**12345**  
**12345**  
**Changing pointer \- passed by reference:**  
**12345**  
**12345 ABCDE**  
**Passing by return value:**  
**12345 ABCDE**   
## Try パターン メソッド  
  
### 説明  
 **実行\<何か\>** パターンを、<xref:System.Int32.TryParse%2A?displayProperty=fullName>など\) を実装するメソッドでは、この違反を発生させません。  <xref:System.Int32.TryParse%2A?displayProperty=fullName> メソッドを実装する構造体 \(値型\) を次の例に示します。  
  
### コード  
 [!CODE [FxCop.Design.TryPattern#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.TryPattern#1)]  
  
## 関連規則  
 [CA1045: 型を参照によって渡しません](../code-quality/ca1045-do-not-pass-types-by-reference.md)