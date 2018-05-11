---
title: 'CA1822: メンバーを static に設定します'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkMembersAsStatic
- CA1822
helpviewer_keywords:
- MarkMembersAsStatic
- CA1822
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 498a3638a02891683aff1b343431418d1a82bab0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ca1822-mark-members-as-static"></a>CA1822: メンバーを static に設定します
|||
|-|-|
|TypeName|MarkMembersAsStatic|
|CheckId|CA1822|
|カテゴリ|Microsoft.Performance|
|互換性に影響する変更点|以外の区切りメンバーが、アセンブリの外側に表示されていない場合、変更に関係なくすること。 なし - とインスタンス メンバーへのメンバーだけを変更する場合、`this`キーワード。<br /><br /> 互換性に影響する、インスタンス メンバーから静的メンバーに、メンバーを変更して、アセンブリ外部から参照である場合。|

## <a name="cause"></a>原因
 インスタンス データにアクセスしないメンバーが静的とマークされていません (内の共有[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)])。

## <a name="rule-description"></a>規則の説明
 インスタンス データにアクセスしない、またはインスタンス メソッドを呼び出さないメンバーは、静的 ([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では共有) としてマークできます。 メソッドを静的としてマークすると、コンパイラはこれらのメンバーに対する非仮想呼び出しサイトを出力します。 非仮想呼び出しサイトの出力と、現在のオブジェクト ポインターが null 以外であることを確認して、各呼び出しの実行時のチェックができなくなります。 これにより、パフォーマンス重視のコードの測定可能なパフォーマンスの向上を実現します。 場合によってでは、現在のオブジェクト インスタンスにアクセスできなかった際は、正確性に関する問題を表します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 静的メンバーをマーク (内の共有または[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) または 'this' を使用して/body 'Me' メソッドで、該当する場合。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 修正プログラムは、重大な変更になりますが、以前にリリース済みコードのこの規則による警告を抑制しても安全です。

## <a name="related-rules"></a>関連規則
 [CA1811: 呼び出されていないプライベート コードを使用しません](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: インスタンス化されていない内部クラスを使用しないでください](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804: 使用されていないローカルを削除します](../code-quality/ca1804-remove-unused-locals.md)