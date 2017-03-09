---
title: "CA2114: メソッドのセキュリティは型のスーパーセットにします | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MethodSecurityShouldBeASupersetOfType"
  - "CA2114"
helpviewer_keywords: 
  - "CA2114"
  - "MethodSecurityShouldBeASupersetOfType"
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2114: メソッドのセキュリティは型のスーパーセットにします
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MethodSecurityShouldBeASupersetOfType|  
|CheckId|CA2114|  
|分類|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## 原因  
 型に宣言セキュリティがあり、その型のメソッドが同じセキュリティ アクションの宣言セキュリティを持ち、セキュリティ アクションが[リンク確認要求](../Topic/Link%20Demands.md)または[Inheritance Demands](http://msdn.microsoft.com/ja-jp/28b9adbb-8f08-4f10-b856-dbf59eb932d9)ではなく、型でチェックされているアクセス許可はメソッドでチェックされているアクセス許可のサブセットではありません。  
  
## 規則の説明  
 メソッドには、同じアクションについて、メソッド レベルと型レベルの宣言セキュリティのいずれも含めないでください。  2 つのチェックは結合されず、メソッド レベルの要求のみが適用されます。  たとえば、型からアクセス許可 `X` が要求され、その型のメソッドのいずれかがアクセス許可 `Y` を要求した場合、メソッドを実行するときにアクセス許可 `X` は必要ありません。  
  
## 違反の修正方法  
 コードに両方のアクションが必要かどうかを再確認します。  両方のアクションが必要な場合、メソッド レベルのアクションに型レベルで指定したセキュリティが含まれるようにします。  たとえば、型でアクセス許可 `X` を要求し、メソッドではアクセス許可 `Y` も必要である場合、メソッドでは、明示的に `X` と `Y` を要求します。  
  
## 警告を抑制する状況  
 型で指定したセキュリティがメソッドに必要ない場合は、この規則による警告を抑制しても安全です。  ただし、これは通常の場合には該当しないため、デザインを十分に確認することをお勧めします。  
  
## 使用例  
 次の例では、この規則に違反する危険性を説明するために、環境のアクセス許可を使用しています。  このアプリケーション コードでは、型に要求されたアクセス許可を拒否する前に、安全な型のインスタンスを作成します。  実際に考えられる脅威に対処するには、別の方法でオブジェクトのインスタンスを取得する必要があります。  
  
 次の例では、ライブラリから型の書き込み許可とメソッドの読み取り許可を要求します。  
  
 [!code-cs[FxCop.Security.MethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_1.cs)]  
  
## 使用例  
 次の例は、メソッドで型レベルのセキュリティ要件に適合していないのにメソッドを呼び出した場合の、ライブラリの脆弱性を示すアプリケーション コードです。  
  
 [!code-cs[FxCop.Security.TestMethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_2.cs)]  
  
 この例を実行すると、次の出力が生成されます。  
  
  **\[All permissions\] Personal information: 6\/16\/1964 12:00:00 AM**  
**\[No write permission \(demanded by type\)\] Personal information: 6\/16\/1964 12:00:00 AM**  
**\[No read permission \(demanded by method\)\] Could not access personal information: Request failed.**   
## 参照  
 [安全なコーディングのガイドライン](../Topic/Secure%20Coding%20Guidelines.md)   
 [Inheritance Demands](http://msdn.microsoft.com/ja-jp/28b9adbb-8f08-4f10-b856-dbf59eb932d9)   
 [リンク確認要求](../Topic/Link%20Demands.md)   
 [データとモデリング](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)