---
title: "CA1060: 移動 P-起動を NativeMethods クラス |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
helpviewer_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
ms.assetid: 06686c8c-6ad3-42f7-a355-cbaefa347cfc
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7805710c61e6a9fcf4ede2ebcbf69589b53141f9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca1060-move-pinvokes-to-nativemethods-class"></a>CA1060: P/Invoke を NativeMethods クラスに移動します
|||  
|-|-|  
|TypeName|MovePInvokesToNativeMethodsClass|  
|CheckId|CA1060|  
|カテゴリ|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 メソッドがアンマネージ コードへのアクセス プラットフォーム呼び出しサービスを使用してのいずれかのメンバーではない、 **NativeMethods**クラスです。  
  
## <a name="rule-description"></a>規則の説明  
 プラットフォーム呼び出しメソッドを使用してマークされているなど、<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>属性、またはを使用して定義されているメソッド、`Declare`キーワード[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]、アンマネージ コードにアクセスします。 これらのメソッドは、次のクラスのいずれかにする必要があります。  
  
-   **NativeMethods** -このクラスがアンマネージ コードのアクセス許可のスタック ウォークを抑制していません。 (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>このクラスに適用する必要がありません)。このクラスは、使用できる任意の場所スタック ウォークを実行するためのメソッドです。  
  
-   **SafeNativeMethods** -このクラスがアンマネージ コードのアクセス許可のスタック ウォークを抑制します。 (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>はこのクラスに適用します)。このクラスは、だれが呼び出しても安全な方法です。 これらのメソッドの呼び出し元は、任意の呼び出し元が無害な方法であるため、使用法が安全であるかどうかを確認する完全なセキュリティ レビューを実行する必要はありません。  
  
-   **UnsafeNativeMethods** -このクラスがアンマネージ コードのアクセス許可のスタック ウォークを抑制します。 (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>はこのクラスに適用します)。このクラスは、潜在的に危険なメソッドをします。 これらのメソッドの呼び出し元は、スタック ウォークは実行されませんので使用法が安全であるかどうかを確認するための完全なセキュリティ レビューを実行する必要があります。  
  
 としてこれらのクラスが宣言されている`internal`(`Friend`、Visual Basic で) し、新しいインスタンスが作成されないように、プライベート コンス トラクターを宣言します。 これらのクラスのメソッドは、必要があります`static`と`internal`(`Shared`と`Friend`Visual Basic で)。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、適切なメソッドを移動**NativeMethods**クラスです。 ほとんどのアプリケーションはという新しいクラスへの P/invoke を移動します。 **NativeMethods**で十分です。  
  
 ただし、他のアプリケーションで使用するためのライブラリを開発している場合は、する必要がありますと呼ばれるその他の 2 つのクラスを定義する**SafeNativeMethods**と**UnsafeNativeMethods**です。 これらのクラスに似ています、 **NativeMethods**クラスです。 ただし、と呼ばれる特別な属性を使用してマークされている**SuppressUnmanagedCodeSecurityAttribute**です。 ランタイムがすべての呼び出し元があるかどうかを確認する完全なスタック ウォークを実行しないこの属性を適用すると、 **UnmanagedCode**権限です。 ランタイムは、通常、起動時にこのアクセス許可を確認します。 チェックが行われないため、これらのアンマネージ メソッドを呼び出す際のパフォーマンスを大幅に向上することができます、コードをこれらのメソッドを呼び出すアクセス許可が制限されていることもできます。  
  
 ただし、慎重にこの属性を使用する必要があります。 重大なセキュリティへの影響にそれが正しく実装されていない場合.  
  
 メソッドを実装する方法については、次を参照してください。、 **NativeMethods**例では、 **SafeNativeMethods**例では、と**UnsafeNativeMethods**例です。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## <a name="example"></a>例  
 次の例では、この規則に違反するメソッドを宣言します。 違反を解決するのには**RemoveDirectory** P/invoke は P/invoke のみを保持するように設計された適切なクラスに移動する必要があります。  
  
 [!code-vb[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_1.vb)]
 [!code-csharp[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_1.cs)]  
  
## <a name="nativemethods-example"></a>NativeMethods 例  
  
### <a name="description"></a>説明  
 **NativeMethods**クラスを使用してマークしないで**SuppressUnmanagedCodeSecurityAttribute**が必要になりますが格納される P/invoke **UnmanagedCode**アクセス許可。 ほとんどのアプリケーションがローカル コンピューターから実行ため、完全な信頼と共に実行すると、これが通常問題になりません。 ただし、再利用可能なライブラリを開発している場合は、する必要がありますを定義する、 **SafeNativeMethods**または**UnsafeNativeMethods**クラスです。  
  
 次の例は、 **Interaction.Beep**をラップするメソッド、 **MessageBeep** user32.dll から関数。 **MessageBeep** P/invoke を配置、 **NativeMethods**クラスです。  
  
### <a name="code"></a>コード  
 [!code-csharp[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_2.cs)]
 [!code-vb[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_2.vb)]  
  
## <a name="safenativemethods-example"></a>SafeNativeMethods 例  
  
### <a name="description"></a>説明  
 任意のアプリケーションに安全に公開して、副次的な影響がなく、P/invoke メソッドはクラスという名前を付ける必要があります**SafeNativeMethods**です。 アクセス許可を要求する必要はありませんしから呼び出されたに多くの注意を払う必要はありません。  
  
 次の例は、 **Environment.TickCount**プロパティをラップする、 **GetTickCount** kernel32.dll から関数。  
  
### <a name="code"></a>コード  
 [!code-vb[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_3.vb)]
 [!code-csharp[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_3.cs)]  
  
## <a name="unsafenativemethods-example"></a>UnsafeNativeMethods 例  
  
### <a name="description"></a>説明  
 P/invoke メソッドを安全に呼び出すし、副作用が発生する可能性がありますはクラスという名前を付ける必要があります**UnsafeNativeMethods**です。 これらのメソッドは、これらは、ユーザーに意図せずになっていることを確認する厳密にチェックする必要があります。 ルール[CA2118: レビュー SuppressUnmanagedCodeSecurityAttribute の使用法](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)を利用しています。 メソッドがの代わりに要求される別のアクセス許可を持つ別の方法として、 **UnmanagedCode**それらを活用するとします。  
  
 次の例は、 **Cursor.Hide**をラップするメソッド、 **ShowCursor** user32.dll から関数。  
  
### <a name="code"></a>コード  
 [!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_4.vb)]
 [!code-csharp[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_4.cs)]  
  
## <a name="see-also"></a>参照  
 [デザインの警告](../code-quality/design-warnings.md)