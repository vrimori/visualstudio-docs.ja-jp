---
title: 'Ca 1057: 文字列 URI オーバー ロードは、System.Uri オーバー ロードを呼び出す |Microsoft Docs'
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
- CA1057
- StringUriOverloadsCallSystemUriOverloads
helpviewer_keywords:
- StringUriOverloadsCallSystemUriOverloads
- CA1057
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e428d0a6353eb5f8f8827dcf5581a41c6ab9a467
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263784"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057: 文字列 URI オーバーロードが、System.Uri オーバーロードを呼び出します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 型宣言が、指定された文字列をパラメーターの置換でのみ異なるメソッドのオーバー ロードを<xref:System.Uri?displayProperty=fullName>パラメーター、および文字列パラメーターを受け取るオーバー ロードは使用するオーバー ロードを呼び出しません、<xref:System.Uri>パラメーター。

## <a name="rule-description"></a>規則の説明
 オーバー ロードは、文字列でのみが異なるため、/<xref:System.Uri>パラメーター文字列が uniform resource identifier (URI) を表すと見なされます。 URI の文字列表現は解析エラーやエンコーディング エラーが発生しやすく、セキュリティ上の脆弱性の原因となる場合があります。 <xref:System.Uri>クラスは、安全かつセキュリティで保護された方法でこれらのサービスを提供します。 メリットを得るため、<xref:System.Uri>文字列オーバー ロードを呼び出す必要があります、クラス、<xref:System.Uri>文字列引数を使用するオーバー ロードします。

## <a name="how-to-fix-violations"></a>違反の修正方法
 インスタンスを作成できるように、URI の文字列表現を使用するメソッドを再実装、<xref:System.Uri>クラスの文字列引数を使用し、渡します、<xref:System.Uri>を持つオーバー ロードするオブジェクト、<xref:System.Uri>パラメーター。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 文字列パラメーターが URI を表していない場合、この規則による警告を抑制するのには安全です。

## <a name="example"></a>例
 次の例では、正しく実装されている文字列オーバー ロードを示します。

 [!code-cpp[FxCop.Design.CallUriOverload#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cpp/FxCop.Design.CallUriOverload.cpp#1)]
 [!code-csharp[FxCop.Design.CallUriOverload#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cs/FxCop.Design.CallUriOverload.cs#1)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/vb/FxCop.Design.CallUriOverload.vb#1)]

## <a name="related-rules"></a>関連規則
 [CA2234: 文字列の代わりに System.Uri オブジェクトを渡します](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1056: URI プロパティを文字列にすることはできません](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: URI パラメーターを文字列にすることはできません](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: URI 戻り値を文字列にすることはできません](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)



