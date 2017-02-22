---
title: "CA1045: 型を参照によって渡しません | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1045"
  - "DoNotPassTypesByReference"
helpviewer_keywords: 
  - "CA1045"
  - "DoNotPassTypesByReference"
ms.assetid: bcc3900a-e092-4bb8-896f-cb83f6289968
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1045: 型を参照によって渡しません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotPassTypesByReference|  
|CheckId|CA1045|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## 原因  
 パブリック型のパブリック メソッドまたはプロテクト メソッドに、プリミティブ型、参照型、または組み込み型ではない値型を使用する `ref` パラメーターがあります。  
  
## 規則の説明  
 \(`out` または `ref` を使用した\) 型の参照渡しには、ポインターの使用経験、値の型と参照型の違いの理解、および複数の戻り値を持つメソッドの処理が必要です。  また、`out` パラメーターと `ref` パラメーターの違いがあまり理解されていません。  
  
 参照型の "参照" 渡しの場合、メソッドは、オブジェクトの別のインスタンスを返すパラメーターを使用しようとします。参照型の参照渡しは、ダブル ポインターの使用、ポインターへのポインター、または二重の間接参照とも呼ばれます。既定の呼び出し規約では、"値" 渡しですが、参照型を使用するパラメーターは、既にオブジェクトに対するポインターを受け取っています。  ポインター \(指し示す先のオブジェクトではなく\) は、値渡しです。  値渡しとは、メソッドで、ポインターの指し示す先を新しいインスタンスの参照型に変更できなくても、指し示す先のオブジェクトのコンテンツは変更できるということです。  ほとんどのアプリケーションは値渡しで十分で、目的の動作を実現できます。  
  
 メソッドで異なるインスタンスを返す必要がある場合、メソッドの戻り値を使用して実現します。  文字列を操作するさまざまなメソッドの <xref:System.String?displayProperty=fullName> クラスを参照して、文字列の新しいインスタンスを返します。  呼び出し元は、このモデルを使用して元のオブジェクトが保存されているかどうかを判断します。  
  
 戻り値は一般的であり、よく使用されますが、`out` パラメーターと `ref` パラメーターを適切に使用する場合、中間のデザインとコーディング技術が必要です。  開発者全般に向けてライブラリをデザインする場合、ユーザーが `out` パラメーターまたは `ref` パラメーターの扱い方を習得することは期待しないでください。  
  
> [!NOTE]
>  大きな構造体であるパラメーターを扱う場合、そのような構造体をコピーするために追加のリソースが必要になるため、値を渡すときにパフォーマンスの低下を招くことがあります。  この場合、`ref` パラメーターまたは `out` パラメーターを使用することをお勧めします。  
  
## 違反の修正方法  
 値型によって発生したこの規則違反を修正するには、メソッドからオブジェクトを戻り値として返すようにします。  メソッドで複数の値を返す必要がある場合、値を保持しているオブジェクトの 1 インスタンスを返すようにメソッドをデザインし直します。  
  
 参照型によって発生したこの規則違反を修正するには、目的の動作が参照の新しいインスタンスを返すことであることを確認します。  この場合、メソッドで戻り値を使用して実行します。  
  
## 警告を抑制する状況  
 この規則による警告を抑制しても安全ですが、このデザインのままでは操作性の問題が発生することがあります。  
  
## 使用例  
 次のライブラリで、ユーザーのフィードバックに対して応答を生成するクラスの実装例を 2 つ示します。  最初の実装 \(`BadRefAndOut`\) によって、ライブラリ ユーザーは 3 つの戻り値を管理することになります。  2 つ目の実装 \(`RedesignedRefAndOut`\) は、ユーザー エクスペリエンスをわかりやすいものにします。これは、データを単体のユニットとして管理するコンテナー クラスのインスタンス \(`ReplyData`\) を返すことで実現しています。  
  
 [!code-cs[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_1.cs)]  
  
## 使用例  
 次のアプリケーションは、ユーザー エクスペリエンスを説明した例です。  再デザインしたライブラリの呼び出し \(`UseTheSimplifiedClass` メソッド\) はわかりやすく、このメソッドで返される情報は管理が容易です。  2 つのメソッドの出力結果は同じです。  
  
 [!code-cs[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_2.cs)]  
  
## 使用例  
 次のライブラリ例は、参照型の `ref` パラメーターの使用方法を示します。また、この機能の実装方法を改善しています。  
  
 [!code-cs[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_3.cs)]  
  
## 使用例  
 次のアプリケーションでは、ライブラリの各メソッドの動作を説明するために、それぞれを呼び出しています。  
  
 [!code-cs[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_4.cs)]  
  
 この例を実行すると、次の出力が生成されます。  
  
  **Changing pointer \- passed by value:**  
**12345**  
**12345**  
**Changing pointer \- passed by reference:**  
**12345**  
**12345 ABCDE**  
**Passing by return value:**  
**12345 ABCDE**   
## 関連規則  
 [CA1021: out パラメーターを使用しません](../code-quality/ca1021-avoid-out-parameters.md)