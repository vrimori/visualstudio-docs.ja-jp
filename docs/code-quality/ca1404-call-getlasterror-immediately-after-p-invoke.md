---
title: "CA1404: P/Invoke の直後に GetLastError を呼び出します | Microsoft Docs"
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
  - "CallGetLastErrorImmediatelyAfterPInvoke"
  - "CA1404"
helpviewer_keywords: 
  - "CallGetLastErrorImmediatelyAfterPInvoke"
  - "CA1404"
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1404: P/Invoke の直後に GetLastError を呼び出します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|  
|CheckId|CA1404|  
|分類|Microsoft.Interoperability|  
|互換性に影響する変更点|なし|  
  
## 原因  
 <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> メソッドまたは同等の Win32 `GetLastError` 関数が呼び出されました。その直前に、プラットフォーム呼び出しメソッドが呼び出されていません。  
  
## 規則の説明  
 プラットフォーム呼び出しメソッドは、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] の `Declare` キーワードまたは <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> 属性を使用して、アンマネージ コードにアクセスし、定義されます。  一般に、エラーが発生した場合、アンマネージ関数は Win32 の `SetLastError` 関数を呼び出し、そのエラーに関連付けられたエラー コードを設定します。  エラーが発生した関数の呼び出し元は、Win32 の `GetLastError` 関数を呼び出してエラー コードを取得し、エラーの原因を判断します。  エラー コードはスレッドごとに保持され、`SetLastError` を次に呼び出すと上書きされます。  マネージ コードでは、エラーの発生したプラットフォーム呼び出しメソッドの呼び出し後に、<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> メソッドを呼び出してエラー コードを取得できます。  エラー コードは、他のマネージ クラス ライブラリのメソッドからの内部的な呼び出しによって上書きできます。そのため、`GetLastError` または <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> メソッドは、プラットフォーム呼び出しメソッドを呼び出した直後に呼び出す必要があります。  
  
 次のマネージ メンバーに対する呼び出しが、プラットフォーム呼び出しメソッドと <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> の呼び出しの間に発生した場合、この規則では無視されます。  このようなメンバーによって、エラー コードは変化しないため、一部のプラットフォーム呼び出しメソッドの呼び出しが成功したことを判断するときに役立ちます。  
  
-   <xref:System.IntPtr.Zero?displayProperty=fullName>  
  
-   <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>  
  
-   <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>  
  
-   <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>  
  
## 違反の修正方法  
 この規則違反を修正するには、<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> の呼び出しを、プラットフォーム呼び出しメソッドの呼び出しの直後に移動します。  
  
## 警告を抑制する状況  
 プラットフォーム呼び出しメソッドの呼び出しと <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> メソッドの呼び出しの間にあるコードによって、エラー コードが明示的または暗黙的に変更されない場合は、この規則による警告を抑制しても安全です。  
  
## 使用例  
 この規則に違反しているメソッドと、規則に適合するメソッドを次の例に示します。  
  
 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/VisualBasic/ca1404-call-getlasterror-immediately-after-p-invoke_1.vb)]
 [!code-cs[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/CSharp/ca1404-call-getlasterror-immediately-after-p-invoke_1.cs)]  
  
## 関連規則  
 [CA1060: P\/Invoke を NativeMethods クラスに移動します](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)  
  
 [CA1400: P\/Invoke エントリ ポイントは存在しなければなりません](../Topic/CA1400:%20P-Invoke%20entry%20points%20should%20exist.md)  
  
 [CA1401: P\/Invoke は参照可能になりません](../Topic/CA1401:%20P-Invokes%20should%20not%20be%20visible.md)  
  
 [CA2101: P\/Invoke 文字列引数に対してマーシャリングを指定します](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)  
  
 [CA2205: Win32 API に相当するマネージ API を使用します](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)