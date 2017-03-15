---
title: "CA1410: COM 登録メソッドは一致しなければなりません | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1410"
  - "ComRegistrationMethodsShouldBeMatched"
helpviewer_keywords: 
  - "CA1410"
  - "ComRegistrationMethodsShouldBeMatched"
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1410: COM 登録メソッドは一致しなければなりません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ComRegistrationMethodsShouldBeMatched|  
|CheckId|CA1410|  
|分類|Microsoft.Interoperability|  
|互換性に影響する変更点|なし|  
  
## 原因  
 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> 属性でマークされたメソッドが型で宣言されているが、<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> 属性でマークされたメソッドが宣言されていません。または、その逆の状態になっています。  
  
## 規則の説明  
 コンポーネント オブジェクト モデル \(COM: Component Object Model\) クライアントで [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 型を作成するには、最初に型を登録する必要があります。  型が使用できる場合、登録プロセスで <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> 属性でマークされたメソッドが呼び出され、ユーザーの指定したコードを実行します。  登録解除プロセスでは <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> 属性でマークされた対応するメソッドが呼び出され、登録メソッドの操作を元に戻します。  
  
## 違反の修正方法  
 この規則違反を修正するには、対応する登録メソッドまたは登録解除メソッドを追加します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 使用例  
 この規則に違反する型を次の例に示します。  コード内のコメントに、違反の修正方法を示します。  
  
 [!code-cs[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/CSharp/ca1410-com-registration-methods-should-be-matched_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/VisualBasic/ca1410-com-registration-methods-should-be-matched_1.vb)]  
  
## 関連規則  
 [CA1411: COM 登録メソッドは参照可能であることはできません](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)  
  
## 参照  
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>   
 [COM へのアセンブリの登録](../Topic/Registering%20Assemblies%20with%20COM.md)   
 [Regasm.exe \(アセンブリ登録ツール\)](../Topic/Regasm.exe%20\(Assembly%20Registration%20Tool\).md)