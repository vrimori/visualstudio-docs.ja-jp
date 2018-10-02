---
title: 'CA1060: 移動 P/invoke を NativeMethods クラスに |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
helpviewer_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
ms.assetid: 06686c8c-6ad3-42f7-a355-cbaefa347cfc
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c2a198a7ff34900d97bca509690bb4e2d8e85f08
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589681"
---
# <a name="ca1060-move-pinvokes-to-nativemethods-class"></a>CA1060: P/Invoke を NativeMethods クラスに移動します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[CA1060: 移動 P/invoke を NativeMethods クラスに](https://docs.microsoft.com/visualstudio/code-quality/ca1060-move-p-invokes-to-nativemethods-class)します。

|||
|-|-|
|TypeName|MovePInvokesToNativeMethodsClass|
|CheckId|CA1060|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 メソッドはアンマネージ コードへのアクセス プラットフォーム呼び出しサービスを使用してのいずれかのメンバーではない、 **NativeMethods**クラス。

## <a name="rule-description"></a>規則の説明
 使用してマークされているなどのプラットフォーム呼び出しメソッド、<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>属性、またはを使用して定義されているメソッド、`Declare`キーワード[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]、アンマネージ コードにアクセスします。 次のクラスのいずれかでこれらのメソッドがあります。

-   **NativeMethods** -このクラスがアンマネージ コード アクセス許可のスタック ウォークを抑制できません。 (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>このクラスに適用する必要がありません)。このクラスでは、メソッドのスタック ウォークを実行するため、どこでも使用できます。

-   **SafeNativeMethods** -このクラスがアンマネージ コード アクセス許可のスタック ウォークを抑制します。 (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>このクラスに適用されます)。このクラスは、メソッドを呼び出すすべてのユーザーに対して安全なは。 これらのメソッドの呼び出し元は、呼び出し元の害のない方法であるため、使用量が安全であるかどうかを確認する完全なセキュリティ レビューを実行する必要はありません。

-   **UnsafeNativeMethods** -このクラスがアンマネージ コード アクセス許可のスタック ウォークを抑制します。 (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>このクラスに適用されます)。このクラスは、危険なメソッドです。 これらのメソッドの呼び出し元は、スタック ウォークは実行しないため、使用量が安全であるかどうかを確認する完全なセキュリティ レビューを実行する必要があります。

 としてこれらのクラスが宣言されている`internal`(`Friend`、Visual Basic で) し、新しいインスタンスが作成されないようにする、プライベート コンス トラクターを宣言します。 これらのクラスのメソッドにする必要があります`static`と`internal`(`Shared`と`Friend`Visual Basic で)。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、適切なメソッドを移動**NativeMethods**クラス。 ほとんどのアプリケーションで P/invoke を移動という新しいクラスに**NativeMethods**十分です。

 ただし、他のアプリケーションで使用するライブラリを開発している場合は、検討するくださいと呼ばれるその他の 2 つのクラスを定義する**SafeNativeMethods**と**UnsafeNativeMethods**します。 これらのクラスのように、 **NativeMethods**クラス。 ただし、と呼ばれる特殊な属性を使用してマークされている**SuppressUnmanagedCodeSecurityAttribute**します。 この属性が適用されるときに、ランタイムがすべての呼び出し元があることを確認する完全なスタック ウォークを実行しない、 **UnmanagedCode**権限。 ランタイムは、通常、起動時にこのアクセス許可をチェックします。 チェックが実行されないため、これらのアンマネージ メソッドを呼び出す際のパフォーマンスを大幅に向上することができます、コードをこれらのメソッドを呼び出すアクセス許可が制限されていることもできます。

 ただし、十分に注意して、この属性を使用する必要があります。 これが正しく実装されていない場合、重大なセキュリティへの影響ができます.

 メソッドを実装する方法については、次を参照してください。、 **NativeMethods**例では、 **SafeNativeMethods**例では、と**UnsafeNativeMethods**例。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、この規則に違反するメソッドを宣言します。 違反を修正する、 **RemoveDirectory** P/invoke は、P/invoke のみを保持するように設計された適切なクラスに移動する必要があります。

 [!code-csharp[FxCop.Design.DllImportNativeMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.DllImportNativeMethods/cs/FxCop.Design.DllImportNativeMethods.cs#1)]
 [!code-vb[FxCop.Design.DllImportNativeMethods#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DllImportNativeMethods/vb/FxCop.Design.DllImportNativeMethods.vb#1)]

## <a name="nativemethods-example"></a>NativeMethods 例

### <a name="description"></a>説明
 **NativeMethods**クラスを使用してマークしないで**SuppressUnmanagedCodeSecurityAttribute**が必要になりますが格納される P/invoke **UnmanagedCode**アクセス許可。 ローカル コンピューターからほとんどのアプリケーションが実行され、完全な信頼と一緒に実行すると、この問題には、通常は。 ただし、再利用可能なライブラリを開発している場合は、する必要がありますを定義する、 **SafeNativeMethods**または**UnsafeNativeMethods**クラス。

 次の例は、 **Interaction.Beep**をラップするメソッド、 **MessageBeep** user32.dll から関数。 **MessageBeep** P/invoke は、配置、 **NativeMethods**クラス。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Design.NativeMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethods/cs/FxCop.Design.NativeMethods.cs#1)]
 [!code-vb[FxCop.Design.NativeMethods#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethods/vb/FxCop.Design.NativeMethods.vb#1)]

## <a name="safenativemethods-example"></a>SafeNativeMethods 例

### <a name="description"></a>説明
 任意のアプリケーションに安全に公開して、副作用がない、P/invoke メソッドは、というクラスに配置する必要があります**SafeNativeMethods**します。 アクセス許可を要求する必要はありませんしから呼び出されたに多くの注意を払う必要はありません。

 次の例は、 **Environment.TickCount**プロパティをラップする、 **GetTickCount**関数を kernel32.dll から。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Design.NativeMethodsSafe#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsSafe/cs/FxCop.Design.NativeMethodsSafe.cs#1)]
 [!code-vb[FxCop.Design.NativeMethodsSafe#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsSafe/vb/FxCop.Design.NativeMethodsSafe.vb#1)]

## <a name="unsafenativemethods-example"></a>UnsafeNativeMethods の例

### <a name="description"></a>説明
 という名前のクラスでは P/invoke メソッドを安全に呼び出すし、副作用を引き起こす可能性を含める必要があります**UnsafeNativeMethods**します。 これらのメソッドは、これらは、ユーザーに意図せずになっていることを確認する厳密にチェックする必要があります。 ルール[CA2118: レビュー SuppressUnmanagedCodeSecurityAttribute の使用法](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)これを支援できます。 代わりに要求されるもう 1 つのアクセスを許可するメソッドが代わりに、あります**UnmanagedCode**に使用するとします。

 次の例は、 **Cursor.Hide**をラップするメソッド、 **ShowCursor** user32.dll から関数。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Design.NativeMethodsUnsafe#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsUnsafe/cs/FxCop.Design.NativeMethodsUnsafe.cs#1)]
 [!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsUnsafe/vb/FxCop.Design.NativeMethodsUnsafe.vb#1)]

## <a name="see-also"></a>関連項目
 [デザインの警告](../code-quality/design-warnings.md)



