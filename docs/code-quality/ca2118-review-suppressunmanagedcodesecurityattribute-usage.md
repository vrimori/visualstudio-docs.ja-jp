---
title: CA2118:SuppressUnmanagedCodeSecurityAttribute の使用法を確認してください
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 092ac7599b0cfb715019a6a9894d845dc47747fc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54959058"
---
# <a name="ca2118-review-suppressunmanagedcodesecurityattribute-usage"></a>CA2118:SuppressUnmanagedCodeSecurityAttribute の使用法を確認してください

|||
|-|-|
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|
|CheckId|CA2118|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリックまたはプロテクト型またはメンバーが、<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>属性。

## <a name="rule-description"></a>規則の説明
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> COM 相互運用またはプラットフォーム呼び出しを使用してアンマネージ コードを実行するメンバーの既定のセキュリティ システムの動作を変更します。 一般的に、システムには、[データとモデリング](/dotnet/framework/data/index)のアンマネージ コード アクセス許可。 この要求は、メンバーのすべての呼び出しの実行時に発生し、アクセス許可のコール スタック内のすべての呼び出し元をチェックします。 システムは、属性が存在するときに、[リンク確認要求](/dotnet/framework/misc/link-demands)アクセス許可の: 呼び出し元が JIT コンパイルされたときに、直前の呼び出し元の権限が確認されます。

 この属性は、主にパフォーマンスを向上するために使用されますが、パフォーマンスが向上するとセキュリティ上のリスクも高くなります。 ネイティブ メソッドを呼び出すパブリック メンバーに属性を配置する場合、呼び出し履歴 (直前の呼び出し元) 以外での呼び出し元はアンマネージ コードのアクセス許可をアンマネージ コードを実行する必要はありません。 パブリック メンバーの操作や入力の処理によって呼び出し元が信頼できるコードに通常制限付きアクセス機能を信頼できないことが可能。

 .NET Framework は、呼び出し元が現在のプロセスのアドレス空間への直接アクセスするを防ぐにはセキュリティ チェックに依存します。 この属性が通常のセキュリティをバイパスするため、コードは、プロセスのメモリに対する読み取りまたは書き込みするために使用できる場合深刻な脅威をもたらします。 リスクは意図的にメモリをプロセスへのアクセスを提供するメソッドに限定されないことに注意してください。どのシナリオでも、悪意のあるコードを実現できますアクセスした場合、たとえば、驚くべきこと、形式が正しくない、または無効な入力を提供することでオンにします。

 またはグループは次のいずれかのメンバーであるが、ローカル コンピューターから実行しない限り、既定のセキュリティ ポリシーは、アセンブリにアンマネージ コード アクセス許可を付与できません。

- コンピューターのゾーンのコード グループ

- Microsoft の厳密な名前のコード グループ

- ECMA 厳密な名前のコード グループ

## <a name="how-to-fix-violations"></a>違反の修正方法
 この属性がどうしても必要なことを確認するようにコードを慎重に確認します。 マネージ コードのセキュリティを使い慣れていらっしゃらないするか、またはこの属性を使用するセキュリティへの影響を理解していない場合は、コードから削除します。 属性が必要な場合は、呼び出し元がコードを悪意を持って使用できないことを確認する必要があります。 コードがアンマネージ コードを実行するアクセス許可を持たない場合、この属性は影響を与えません、削除する必要があります。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 安全にこの規則による警告を抑制するには、ネイティブの操作や、破壊的な方法で使用できるリソースにアクセスを呼び出し元に提供していないことを確認する必要があります。

## <a name="example-1"></a>例 1
 次の例では、この規則に違反します。

 [!code-csharp[FxCop.Security.TypesDoNotSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_1.cs)]

## <a name="example-2"></a>例 2
 次の例では、`DoWork`メソッドは、プラットフォーム呼び出しメソッドをパブリックにアクセスできるコード パスを提供します。`FormatHardDisk`します。

 [!code-csharp[FxCop.Security.PInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_2.cs)]

## <a name="example-3"></a>例 3
 次の例では、パブリック メソッドで`DoDangerousThing`違反が発生します。 違反を解決するのには`DoDangerousThing`プライベートで行う必要がありへのアクセスがセキュリティの要求によって保護されたパブリック メソッドを使用する必要がありますのように、`DoWork`メソッド。

 [!code-csharp[FxCop.Security.TypeInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_3.cs)]

## <a name="see-also"></a>関連項目

- <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>
- [安全なコーディングのガイドライン](/dotnet/standard/security/secure-coding-guidelines)
- [データとモデリング](/dotnet/framework/data/index)
- [リンク確認要求](/dotnet/framework/misc/link-demands)