---
title: 'CA1726: 適切な用語を使用します'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UsePreferredTerms
- CA1726
helpviewer_keywords:
- UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b4f83e7754bcb96de05eac3273133cabbc8b8f61
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ca1726-use-preferred-terms"></a>CA1726: 適切な用語を使用します
|||
|-|-|
|TypeName|UsePreferredTerms|
|CheckId|CA1726|
|カテゴリ|Microsoft.Naming|
|互換性に影響する変更点|– アセンブリで発生した場合<br /><br /> 改行の型パラメーターで発生した場合|

## <a name="cause"></a>原因
 外部から参照可能な識別子の名前に含まれている用語に対応する、別の推奨される用語があります。 また、名前には、フラグまたはフラグという語が含まれています。

## <a name="rule-description"></a>規則の説明
 このルールは、識別子をトークンに解析します。 単一のトークンと連続する 2 つのトークンの組み合わせとカスタム ディクショナリの非推奨のセクションではルールに組み込まれている用語が比較されます。 次の表は、ルールとその推奨される代替手段に組み込まれている条件を示します。

|廃止された用語|推奨用語|
|-------------------|--------------------|
|されない|されません|
|取り消し済み|Canceled|
|できません。|できません。|
|ComPlus|EnterpriseServices|
|Couldnt|でした|
|Didnt|DidNot|
|セーフモード|含まれていません|
|Dont|ください|
|フラグまたはフラグ|置換用語はありません。 使用しないでください。|
|いた|HadNot|
|していません。|妥当|
|していません。|プロファ|
|インデックス|Indexes|
|ありません。|IsNot|
|ログイン|ログオン|
|ログアウト|ログオフ|
|Shouldnt|マクロ|
|サインオン|サインイン|
|サインオフ|サインアウト|
|Wasnt|WasNot|
|でした。|WereNot|
|しない|自分|
|Wouldnt|ユースケース|
|書き込み可能です|書き込み可能です|

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、推奨される代替用語でという用語を置き換えます。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 識別子の名前が意図的なとが推奨される用語ではなく元の用語に特に関連する場合にのみ、この規則による警告を抑制します。

## <a name="related-rules"></a>関連規則
 [名前付けに関する警告](../code-quality/naming-warnings.md)