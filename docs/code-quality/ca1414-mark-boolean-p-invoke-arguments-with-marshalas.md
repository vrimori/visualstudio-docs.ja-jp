---
title: "CA1414: ブール型の P/Invoke 引数を MarshalAs に設定します | Microsoft Docs"
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
  - "CA1414"
  - "MarkBooleanPInvokeArgumentsWithMarshalAs"
helpviewer_keywords: 
  - "CA1414"
  - "MarkBooleanPInvokeArgumentsWithMarshalAs"
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1414: ブール型の P/Invoke 引数を MarshalAs に設定します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|  
|CheckId|CA1414|  
|分類|Microsoft.Interoperability|  
|互換性に影響する変更点|あり|  
  
## 原因  
 プロパティ呼び出しメソッド宣言に <xref:System.Boolean?displayProperty=fullName> パラメーターまたは戻り値が含まれていますが、<xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> 属性がそのパラメーターまたは戻り値に適用されていません。  
  
## 規則の説明  
 プラットフォーム呼び出しメソッドは、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] の `Declare` キーワードまたは <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> を使用して、アンマネージ コードにアクセスし、定義されます。  <xref:System.Runtime.InteropServices.MarshalAsAttribute> は、マネージ コードとアンマネージ コード間のデータ型の変換に使用されるマーシャリング動作を指定します。  <xref:System.Byte?displayProperty=fullName> や <xref:System.Int32?displayProperty=fullName> など、単純なデータ型の多くは、アンマネージ コードの単一の表現を持っており、マーシャリング動作を指定する必要はありません。共通言語ランタイムにより、適切な動作が自動的に提供されます。  
  
 <xref:System.Boolean> データ型は、アンマネージ コードの複数の表現を持っています。  <xref:System.Runtime.InteropServices.MarshalAsAttribute> が指定されていない場合、<xref:System.Boolean> データ型の既定のマーシャリング動作は <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> です。  これは 32 ビット整数であり、すべての状況に適しているわけではありません。  アンマネージ メソッドが必要とするブール型の表現を特定して、適切な <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> に一致させる必要があります。  UnmanagedType.Bool は、Win32 BOOL 型であり、常に 4 バイトです。  UnmanagedType.U1 は、C\+\+ `bool` や他の 1 バイト型に使用します。  詳細については、「[Default Marshaling for Boolean Types](http://msdn.microsoft.com/ja-jp/d4c00537-70f7-4ca6-8197-bfc1ec037ff9)」を参照してください。  
  
## 違反の修正方法  
 この規則の反を修正するには、<xref:System.Runtime.InteropServices.MarshalAsAttribute> を <xref:System.Boolean> パラメーターまたは戻り値に適用します。  属性の値を適切な <xref:System.Runtime.InteropServices.UnmanagedType> に設定します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  既定のマーシャリング動作が適切な場合でも、動作を明示的に指定することにより、コードの保守がさらに簡単になります。  
  
## 使用例  
 次の例は、適切な <xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性でマークされた、2 つのプラットフォーム呼び出しメソッドを示しています。  
  
 [!code-cs[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]  
  
## 関連規則  
 [CA1901: P\/Invoke 宣言はポータブルでなければなりません](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)  
  
 [CA2101: P\/Invoke 文字列引数に対してマーシャリングを指定します](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)  
  
## 参照  
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>   
 [Default Marshaling for Boolean Types](http://msdn.microsoft.com/ja-jp/d4c00537-70f7-4ca6-8197-bfc1ec037ff9)   
 [アンマネージ コードとの相互運用](../Topic/Interoperating%20with%20Unmanaged%20Code.md)