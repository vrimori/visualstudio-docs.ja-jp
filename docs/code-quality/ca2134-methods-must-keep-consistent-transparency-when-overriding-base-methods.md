---
title: "CA2134: メソッドは、基本メソッドをオーバーライドしている場合、透過性の整合性を保つ必要がある | Microsoft Docs"
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
  - "CA2134"
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2134: メソッドは、基本メソッドをオーバーライドしている場合、透過性の整合性を保つ必要がある
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MethodsMustOverrideWithConsistentTransparency|  
|CheckId|CA2134|  
|分類|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## 原因  
 この規則は、<xref:System.Security.SecurityCriticalAttribute> が適用されたメソッドが、透過的メソッドまたは <xref:System.Security.SecuritySafeCriticalAttribute> が適用されたメソッドをオーバーライドした場合に適用されます。  また、透過的メソッドまたは <xref:System.Security.SecuritySafeCriticalAttribute> が適用されたメソッドが、<xref:System.Security.SecurityCriticalAttribute> が適用されたメソッドをオーバーライドした場合も、この規則が適用されます。  
  
 この規則は、仮想メソッドをオーバーライドする場合やインターフェイスを実装する場合に適用されます。  
  
## 規則の説明  
 この規則は、メソッドのセキュリティ アクセシビリティをさらに上位の継承チェーンに変更しようとした場合に適用されます。  たとえば、基本クラス内の仮想メソッドが透過的メソッドまたはセーフ クリティカルなメソッドである場合、透過的メソッドまたはセーフ クリティカルなメソッドを使用して、この仮想メソッドを派生クラス内でオーバーライドする必要があります。  これに対し、この仮想メソッドがセキュリティ クリティカルなメソッドである場合、セキュリティ クリティカルなメソッドを使用して、この仮想メソッドを派生クラス内でオーバーライドする必要があります。  インターフェイス メソッドを実装する場合も、同じ規則が適用されます。  
  
 透過性の計算に動的な型情報が必要ないよう、実行時ではなく JIT でコードがコンパイルされた場合に透過性の規則が適用されます。  そのため、透過性の計算結果は、動的型情報に関係なく、JIT でコンパイルされた静的な型情報だけで定義できるようにする必要があります。  
  
## 違反の修正方法  
 この規則違反を修正するには、仮想メソッドをオーバーライドするメソッドまたはインターフェイスを実装するメソッドの透過性を変更して、仮想メソッドまたはインターフェイス メソッドの透過性に一致させる必要があります。  
  
## 警告を抑制する状況  
 この規則による警告を抑制しないでください。  この規則に違反すると、レベル 2 の透過性を使用するアセンブリに対して、ランタイム例外 <xref:System.TypeLoadException> が発生します。  
  
## 例  
  
### コード  
 [!CODE [FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../CodeSnippet/VS_Snippets_CodeAnalysis/fxcop.security.ca2134.methodsmustoverridewithconsistenttransparency#1)]  
  
## 参照  
 [透過的セキュリティ コード、レベル 2](../Topic/Security-Transparent%20Code,%20Level%202.md)