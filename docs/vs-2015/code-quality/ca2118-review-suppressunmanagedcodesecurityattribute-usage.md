---
title: '2118: ca SuppressUnmanagedCodeSecurityAttribute のレビュー使用法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2118
- ReviewSuppressUnmanagedCodeSecurityUsage
helpviewer_keywords:
- ReviewSuppressUnmanagedCodeSecurityUsage
- CA2118
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6d4cee2d7758f467a13875f89a9534ceb0d883b5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49904480"
---
# <a name="ca2118-review-suppressunmanagedcodesecurityattribute-usage"></a>CA2118: SuppressUnmanagedCodeSecurityAttribute の使用法をレビューします
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|
|CheckId|CA2118|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリックまたはプロテクト型またはメンバーが、<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>属性。

## <a name="rule-description"></a>規則の説明
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> COM 相互運用またはプラットフォーム呼び出しを使用してアンマネージ コードを実行するメンバーの既定のセキュリティ システムの動作を変更します。 一般的に、システムには、[データとモデリング](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)のアンマネージ コード アクセス許可。 この要求は、メンバーのすべての呼び出しの実行時に発生し、アクセス許可のコール スタック内のすべての呼び出し元をチェックします。 システムは、属性が存在するときに、[リンク確認要求](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)アクセス許可の: 呼び出し元が JIT コンパイルされたときに、直前の呼び出し元の権限が確認されます。

 この属性は、主にパフォーマンスを向上するために使用されますが、パフォーマンスが向上するとセキュリティ上のリスクも高くなります。 ネイティブ メソッドを呼び出すパブリック メンバーに属性を配置する場合、呼び出し履歴 (直前の呼び出し元) 以外での呼び出し元はアンマネージ コードのアクセス許可をアンマネージ コードを実行する必要はありません。 パブリック メンバーの操作や入力の処理によって呼び出し元が信頼できるコードに通常制限付きアクセス機能を信頼できないことが可能。

 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]に対する呼び出し元が現在のプロセスのアドレス空間への直接アクセスするを防ぐにはセキュリティ チェックに依存しています。 この属性が通常のセキュリティをバイパスするため、コードは、プロセスのメモリに対する読み取りまたは書き込みするために使用できる場合深刻な脅威をもたらします。 リスクは意図的にメモリをプロセスへのアクセスを提供するメソッドに限定されないことに注意してください。どのシナリオでも、悪意のあるコードを実現できますアクセスした場合、たとえば、驚くべきこと、形式が正しくない、または無効な入力を提供することでオンにします。

 またはグループは次のいずれかのメンバーであるが、ローカル コンピューターから実行しない限り、既定のセキュリティ ポリシーは、アセンブリにアンマネージ コード アクセス許可を付与できません。

-   コンピューターのゾーンのコード グループ

-   Microsoft の厳密な名前のコード グループ

-   ECMA 厳密な名前のコード グループ

## <a name="how-to-fix-violations"></a>違反の修正方法
 この属性がどうしても必要なことを確認するようにコードを慎重に確認します。 マネージ コードのセキュリティを使い慣れていらっしゃらないするか、またはこの属性を使用するセキュリティへの影響を理解していない場合は、コードから削除します。 属性が必要な場合は、呼び出し元がコードを悪意を持って使用できないことを確認する必要があります。 コードがアンマネージ コードを実行するアクセス許可を持たない場合、この属性は影響を与えません、削除する必要があります。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 安全にこの規則による警告を抑制するには、ネイティブの操作や、破壊的な方法で使用できるリソースにアクセスを呼び出し元に提供していないことを確認する必要があります。

## <a name="example"></a>例
 次の例では、この規則に違反します。

 [!code-csharp[FxCop.Security.TypesDoNotSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypesDoNotSuppress/cs/FxCop.Security.TypesDoNotSuppress.cs#1)]

## <a name="example"></a>例
 次の例では、`DoWork`メソッドは、プラットフォーム呼び出しメソッドをパブリックにアクセスできるコード パスを提供します。`FormatHardDisk`します。

 [!code-csharp[FxCop.Security.PInvokeAndSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PInvokeAndSuppress/cs/FxCop.Security.PInvokeAndSuppress.cs#1)]

## <a name="example"></a>例
 次の例では、パブリック メソッドで`DoDangerousThing`違反が発生します。 違反を解決するのには`DoDangerousThing`プライベートで行う必要がありへのアクセスがセキュリティの要求によって保護されたパブリック メソッドを使用する必要がありますのように、`DoWork`メソッド。

 [!code-csharp[FxCop.Security.TypeInvokeAndSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypeInvokeAndSuppress/cs/FxCop.Security.TypeInvokeAndSuppress.cs#1)]

## <a name="see-also"></a>関連項目
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> [安全なコーディングのガイドライン](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)[セキュリティの最適化](http://msdn.microsoft.com/en-us/cf255069-d85d-4de3-914a-e4625215a7c0)[データとモデリング](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)[リンク確認要求](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)



