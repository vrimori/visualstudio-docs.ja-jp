---
title: "CA2144: 透過的コードは、バイト配列からアセンブリを読み込んではならない | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2144"
ms.assetid: 777b1310-6e16-4413-b4ee-5f3136304f82
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# CA2144: 透過的コードは、バイト配列からアセンブリを読み込んではならない
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotLoadAssembliesFromByteArrays|  
|CheckId|CA2144|  
|分類|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## 原因  
 透過的メソッドが、次のいずれかのメソッドを使用してバイト配列からアセンブリを読み込みます。  
  
-   <xref:System.Reflection.Assembly.Load%2A>  
  
-   <xref:System.Reflection.Assembly.Load%2A>  
  
-   <xref:System.Reflection.Assembly.Load%2A>  
  
## 規則の説明  
 透過的なコードはセキュリティ上重要な操作を実行できないため、透過的なコードのセキュリティ レビューは、クリティカル コードのセキュリティ レビューほど完全ではありません。  バイト配列から読み込まれるアセンブリは透過的なコード内で認識されない場合がありますが、監査を必要とする、クリティカルなコード、またはさらに重要であるセーフ クリティカルなコードがそのバイト配列に含まれる可能性があります。  このため、透過的なコードでは、バイト配列からアセンブリを読み込むことはできません。  
  
## 違反の修正方法  
 この規則違反を修正するには、アセンブリを読み込むメソッドに <xref:System.Security.SecurityCriticalAttribute> 属性または <xref:System.Security.SecuritySafeCriticalAttribute> 属性を設定します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 使用例  
 次のコードでは、透過的メソッドでバイト配列からアセンブリを読み込んでいるため、この規則が適用されます。  
  
 [!code-cs[FxCop.Security.CA2144.TransparentMethodsShouldNotLoadAssembliesFromByteArrays#1](../code-quality/codesnippet/CSharp/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays_1.cs)]