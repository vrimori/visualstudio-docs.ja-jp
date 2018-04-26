---
title: 'CA2118: SuppressUnmanagedCodeSecurityAttribute の使用法をレビューします'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2118
- ReviewSuppressUnmanagedCodeSecurityUsage
helpviewer_keywords:
- ReviewSuppressUnmanagedCodeSecurityUsage
- CA2118
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 3eeff4eca5bcc6d2490fc077501726e3ba7e8de1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ca2118-review-suppressunmanagedcodesecurityattribute-usage"></a>CA2118: SuppressUnmanagedCodeSecurityAttribute の使用法をレビューします
|||
|-|-|
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|
|CheckId|CA2118|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリックまたはプロテクト型またはメンバーが、<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>属性。

## <a name="rule-description"></a>規則の説明
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> COM 相互運用またはプラットフォーム呼び出しを使用してアンマネージ コードを実行するメンバーの既定のセキュリティ システムの動作を変更します。 一般に、システムにより、[データとモデリング](/dotnet/framework/data/index)アンマネージ コードのアクセス許可のです。 この要求は、メンバーの呼び出しのたびに、実行時に発生し、アクセス許可の呼び出し履歴内のすべての呼び出し元をチェックします。 システムは、属性が存在する場合、[リンク確認要求](/dotnet/framework/misc/link-demands)のアクセス許可: 呼び出し元が JIT でコンパイルされたときに、直前の呼び出し元の権限はチェックされます。

 この属性は、主にパフォーマンスを向上するために使用されますが、パフォーマンスが向上するとセキュリティ上のリスクも高くなります。 ネイティブ メソッドを呼び出すのパブリック メンバーに属性を配置する場合、(直前の呼び出し元) 以外の呼び出し履歴内の呼び出し元はアンマネージ コードのアクセス許可をアンマネージ コードを実行する必要はありません。 によっては、パブリック メンバーのアクションおよび入力の処理には、信頼できない呼び出し元が信頼できるコードを通常どおりに制限されている機能にアクセスすることが可能です。

 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]に対する呼び出し元が現在のプロセスのアドレス空間に直接アクセスするを防ぐためのセキュリティ チェックに依存しています。 この属性が通常のセキュリティをバイパスするので、コードは、プロセスのメモリに対する読み取りまたは書き込みに使用できる場合、重大な脅威を招きます。 リスクが意図的にメモリをプロセスへのアクセスを提供するメソッドに制限されていないことに注意してください。どのシナリオでも、悪意のあるコードを実現できますアクセスした場合、たとえば、ことにより意外、形式が正しくない、または無効な入力を提供することによって表示もできます。

 ローカル コンピューターから実行する、次のグループのいずれかのメンバーである場合を除き、既定のセキュリティ ポリシーは、アセンブリにアンマネージ コードのアクセス許可を付与されず。

-   コンピューターのゾーンのコード グループ

-   Microsoft 厳密な名前のコード グループ

-   ECMA 厳密な名前のコード グループ

## <a name="how-to-fix-violations"></a>違反の修正方法
 この属性がどうしても必要なことを確認するコードを慎重に確認します。 マネージ コードのセキュリティに習熟していないか、この属性を使用するセキュリティへの影響を理解していない、設定した場合は、コードから削除します。 属性が必要な場合は、呼び出し元がコードを悪意を持って使用できないことを確認する必要があります。 コードがアンマネージ コードを実行するアクセス許可を持たない場合、この属性は影響を与えませんし、削除する必要があります。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告を安全に抑制するには、ネイティブの操作または破壊的な方法で使用できるリソースへのアクセスを呼び出し元に提供していないを確認する必要があります。

## <a name="example"></a>例
 次の例では、この規則に違反します。

 [!code-csharp[FxCop.Security.TypesDoNotSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_1.cs)]

## <a name="example"></a>例
 次の例で、`DoWork`メソッドは、プラットフォーム呼び出しメソッドをパブリックにアクセスできるコード パスを提供`FormatHardDisk`です。

 [!code-csharp[FxCop.Security.PInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_2.cs)]

## <a name="example"></a>例
 次の例では、そのパブリック メソッドで`DoDangerousThing`違反が発生します。 違反を解決するのには`DoDangerousThing`加える必要のあるプライベート、およびに示すようへのアクセス権が、セキュリティ確認要求によって保護されているパブリック メソッドを使用する必要があります、`DoWork`メソッドです。

 [!code-csharp[FxCop.Security.TypeInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_3.cs)]

## <a name="see-also"></a>関連項目
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> [安全なコーディングのガイドライン](/dotnet/standard/security/secure-coding-guidelines)[データとモデリング](/dotnet/framework/data/index)[リンク確認要求](/dotnet/framework/misc/link-demands)
