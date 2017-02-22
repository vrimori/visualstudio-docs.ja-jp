---
title: "CA1065: 予期しない場所に例外を発生させません | Microsoft Docs"
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
  - "CA1065"
  - "DoNotRaiseExceptionsInUnexpectedLocations"
helpviewer_keywords: 
  - "DoNotRaiseExceptionsInUnexpectedLocations"
  - "CA1065"
ms.assetid: 4e1bade4-4ca2-4219-abc3-c7b2d741e157
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1065: 予期しない場所に例外を発生させません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotRaiseExceptionsInUnexpectedLocations|  
|CheckId|CA1065|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|なし|  
  
## 原因  
 例外をスローしないはずのメソッドが例外をスローします。  
  
## 規則の説明  
 例外をスローしないはずのメソッドには、次のような種類があります。  
  
-   プロパティ取得メソッド  
  
-   イベント アクセサー メソッド  
  
-   Equals メソッド  
  
-   GetHashCode メソッド  
  
-   ToString メソッド  
  
-   静的コンストラクター  
  
-   ファイナライザー  
  
-   Dispose メソッド  
  
-   等値演算子  
  
-   暗黙的なキャスト演算子  
  
 以下のセクションでは、これらのメソッドについて説明します。  
  
### プロパティ取得メソッド  
 プロパティは、基本的にはスマート フィールドです。  したがって、できるだけフィールドと同じように動作する必要があります。  フィールドが例外をスローしないのと同様、プロパティも例外をスローしてはなりません。  例外をスローするプロパティがある場合は、そのプロパティをメソッドにすることを検討してください。  
  
 以下の例外はプロパティ取得メソッドからスローできます。  
  
-   <xref:System.InvalidOperationException?displayProperty=fullName> およびすべての派生オブジェクト \(<xref:System.ObjectDisposedException?displayProperty=fullName> を含む\)  
  
-   <xref:System.NotSupportedException?displayProperty=fullName> およびすべての派生オブジェクト  
  
-   <xref:System.ArgumentException?displayProperty=fullName> \(インデックスによる取得の場合のみ\)  
  
-   <xref:System.Collections.Generic.KeyNotFoundException> \(インデックスによる取得の場合のみ\)  
  
### イベント アクセサー メソッド  
 イベント アクセサーは、例外をスローしない単純な操作でなければなりません。  イベントがイベント ハンドラーを追加または削除するときに例外をスローしないようにする必要があります。  
  
 以下の例外はイベント アクセサーからスローできます。  
  
-   <xref:System.InvalidOperationException?displayProperty=fullName> およびすべての派生オブジェクト \(<xref:System.ObjectDisposedException?displayProperty=fullName> を含む\)  
  
-   <xref:System.NotSupportedException?displayProperty=fullName> およびすべての派生オブジェクト  
  
-   <xref:System.ArgumentException> および派生オブジェクト  
  
### Equals メソッド  
 以下の **Equals** メソッドは例外をスローできません。  
  
-   <xref:System.Object.Equals%2A?displayProperty=fullName>  
  
-   [M: IEquatable.Equals](http://go.microsoft.com/fwlink/?LinkId=113472)  
  
 **Equals** メソッドは、例外をスローする代わりに、`true` または `false` を返す必要があります。  たとえば、2 つの一致しない型が渡された場合、Equals は <xref:System.ArgumentException> をスローする代わりに `false` を返す必要があります。  
  
### GetHashCode メソッド  
 以下の **GetHashCode** メソッドは、通常は例外をスローできません。  
  
-   <xref:System.Object.GetHashCode%2A>  
  
-   [M: IEqualityComparer.GetHashCode \(T\)](http://go.microsoft.com/fwlink/?LinkId=113477)  
  
 **GetHashCode**  は常に値を返す必要があります。  そうしなければ、ハッシュ テーブル内の項目が失われる可能性があります。  
  
 **GetHashCode**  のバージョンのうち引数を受け取るものは <xref:System.ArgumentException> をスローできます。  ただし、**Object.GetHashCode** は例外をスローできません。  
  
### ToString メソッド  
 デバッガーは <xref:System.Object.ToString%2A?displayProperty=fullName> を使用してオブジェクトの情報を文字列形式で表示します。  そのため、**ToString**  はオブジェクトの状態を変更してはならず、例外をスローすることもできません。  
  
### 静的コンストラクター  
 静的コンストラクターが例外をスローすると、その型は現在のアプリケーション ドメイン内で使用できなくなります。  明確な理由 \(セキュリティ上の問題など\) がない限り、静的コンストラクターが例外をスローしないようにしてください。  
  
### ファイナライザー  
 ファイナライザーが例外をスローすると、直ちに CLR がエラーとなり、プロセスが終了します。  したがって、どのような場合でもファイナライザーが例外をスローしないようにしてください。  
  
### Dispose メソッド  
 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> メソッドから例外をスローすることはできません。  Dispose は一般に `finally` 句内でクリーンアップ ロジックの一部として呼び出されます。  したがって、Dispose が明示的に例外をスローすると、ユーザーは `finally` 句に例外処理を追加するよう要求されます。  
  
 **Dispose\(false\)** のコード パスが例外をスローしないようにしてください。このメソッドは、ほとんどの場合ファイナライザーから呼び出されるからです。  
  
### 等値演算子 \(\=\=、\!\=\)  
 Equals メソッドと同様に、等値演算子も `true` と `false` のいずれかを返す必要があり、例外をスローすることはできません。  
  
### 暗黙的なキャスト演算子  
 ユーザーは暗黙的なキャスト演算子が呼び出されたことに気付かないことが多いため、暗黙的なキャスト演算子がスローする例外はまったく予測不可能です。  したがって、暗黙的なキャスト演算子が例外をスローしないようにしてください。  
  
## 違反の修正方法  
 プロパティの getter については、例外のスローが不要となるようにロジックを変更するか、プロパティをメソッドに変更します。  
  
 それ以外の上記メソッドについては、例外のスローが不要となるようにロジックを変更します。  
  
## 警告を抑制する状況  
 スローされた例外ではなく例外宣言が原因で違反が発生した場合、この規則による警告を抑制しても安全です。  
  
## 関連規則  
 [CA2219: exception 句に例外を発生させないでください](../Topic/CA2219:%20Do%20not%20raise%20exceptions%20in%20exception%20clauses.md)  
  
## 参照  
 [デザイン上の警告](../code-quality/design-warnings.md)