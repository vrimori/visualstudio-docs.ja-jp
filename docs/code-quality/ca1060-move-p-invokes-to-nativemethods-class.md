---
title: "CA1060: P/Invoke を NativeMethods クラスに移動します | Microsoft Docs"
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
  - "MovePInvokesToNativeMethodsClass"
  - "CA1060"
helpviewer_keywords: 
  - "CA1060"
  - "MovePInvokesToNativeMethodsClass"
ms.assetid: 06686c8c-6ad3-42f7-a355-cbaefa347cfc
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1060: P/Invoke を NativeMethods クラスに移動します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MovePInvokesToNativeMethodsClass|  
|CheckId|CA1060|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## 原因  
 メソッドは、プラットフォーム呼び出しサービスを使用してアンマネージ コードにアクセスしていますが、**NativeMethods** クラスのいずれかのメンバーではありません。  
  
## 規則の説明  
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> 属性を使用してマークされているメソッドなどのプラットフォーム呼び出しメソッド、または [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] で `Declare` キーワードを使用して定義されたメソッドが、アンマネージ コードにアクセスしています。  このメソッドは、次のクラスのいずれかに含まれる必要があります。  
  
-   **NativeMethods** \- このクラスは、アンマネージ コード アクセス許可のスタック ウォークを出力します \(<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> は、このクラスに適用しないでください\)。スタック ウォークを実行するため、このクラスは任意の場所で使用できるメソッドに適しています。  
  
-   **SafeNativeMethods** \- このクラスは、アンマネージ コード アクセス許可のスタック ウォークを出力しません \(<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> は、このクラスに適用されます\)。このクラスは、だれが呼び出しても安全なメソッドに適しています。  だれが呼び出しても安全性の面で問題のないメソッドであるため、このメソッドを呼び出す場合、安全に使用できるようにセキュリティの確認を完全に行う必要はありません。  
  
-   **UnsafeNativeMethods** \- このクラスは、アンマネージ コード アクセス許可のスタック ウォークを出力しません \(<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> は、このクラスに適用されます\)。このクラスは、危険性のあるメソッドに適しています。  スタック ウォークは実行されないため、このメソッドを呼び出す場合、安全に使用できるようにセキュリティの確認を完全に行います。  
  
 このクラスを `internal` \(Visual Basic では `Friend`\) と宣言し、プライベート コンストラクターを宣言して、新しいインスタンスが作成されないようにします。  このクラスのメソッドは、`static` および `internal` \(Visual Basic では `Shared` および `Friend`\) にする必要があります。  
  
## 違反の修正方法  
 この規則違反を修正するには、適切な **NativeMethods** クラスにメソッドを移動します。  ほとんどのアプリケーションでは、P\/Invoke を **NativeMethods** という名前の新しいクラスに移動すれば十分です。  
  
 ただし、他のアプリケーションで使用するライブラリを開発している場合は、**SafeNativeMethods** と **UnsafeNativeMethods** という他の 2 つのクラスを定義することを検討する必要があります。  これらのクラスは **NativeMethods** クラスに類似していますが、**SuppressUnmanagedCodeSecurityAttribute** という特別な属性を使用してマークされています。  この属性が適用される場合、ランタイムで、すべての呼び出し元が **UnmanagedCode** アクセス許可を持つかどうかを確認するための完全なスタック ウォークが実行されません。  通常、ランタイムは起動時にこのアクセス許可をチェックします。  このチェックが実行されないため、これらのアンマネージ メソッドを呼び出す際のパフォーマンスが大幅に向上しています。また、アクセス許可が制限されているコードでこれらのメソッドを呼び出すこともできます。  
  
 ただし、この属性を使用する場合は細心の注意が必要です。  正しく実装しないと、セキュリティに重大な影響を及ぼす可能性があります。  
  
 メソッドを実装する方法については、**NativeMethods**、**SafeNativeMethods**、および **UnsafeNativeMethods** の各例を参照してください。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 使用例  
 この規則に違反するメソッドの宣言例を次に示します。  違反を修正するには、**RemoveDirectory** P\/Invoke を、P\/Invoke のみの格納用に設計されている適切なクラスに移動する必要があります。  
  
 [!code-vb[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_1.vb)]
 [!code-cs[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_1.cs)]  
  
## NativeMethods の例  
  
### 説明  
 **NativeMethods** クラスは **SuppressUnmanagedCodeSecurityAttribute** を使用してマークできないため、このクラスに配置されている P\/Invoke には **UnmanagedCode** アクセス許可が必要です。  ほとんどのアプリケーションはローカル コンピューターから完全信頼で実行されるため、通常、これは問題になりません。  ただし、再利用できるライブラリを開発している場合は、**SafeNativeMethods** クラスまたは **UnsafeNativeMethods** クラスを定義することを検討する必要があります。  
  
 user32.dll の **MessageBeep** 関数をラップする **Interaction.Beep** メソッドの例を次に示します。  **MessageBeep** P\/Invoke は **NativeMethods** クラスに配置されています。  
  
### コード  
 [!code-cs[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_2.cs)]
 [!code-vb[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_2.vb)]  
  
## SafeNativeMethods の例  
  
### 説明  
 アプリケーションに公開しても安全で、副作用がない P\/Invoke メソッドは、**SafeNativeMethods** というクラスに配置する必要があります。  アクセス許可を要求する必要も、呼び出し元に多大な注意を払う必要もありません。  
  
 kernel32.dll の **GetTickCount** 関数をラップする **Environment.TickCount** プロパティの例を次に示します。  
  
### コード  
 [!CODE [FxCop.Design.NativeMethodsSafe#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsSafe#1)]  
  
## UnsafeNativeMethods の例  
  
### 説明  
 呼び出しが安全でなく、副作用が発生する可能性がある P\/Invoke メソッドは、**UnsafeNativeMethods** というクラスに配置する必要があります。  これらのメソッドは、誤ってユーザーに公開されないように厳密にチェックする必要があります。  これには、規則「[CA2118: SuppressUnmanagedCodeSecurityAttribute の使用法を再確認します](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)」が役立ちます。  または、これらのメソッドを使用する場合に、**UnmanagedCode** ではなく、別のアクセス許可を要求する必要があります。  
  
 user32.dll の **ShowCursor** 関数をラップする **Cursor.Hide** メソッドの例を次に示します。  
  
### コード  
 [!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_3.vb)]
 [!code-cs[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_3.cs)]  
  
## 参照  
 [デザイン上の警告](../code-quality/design-warnings.md)