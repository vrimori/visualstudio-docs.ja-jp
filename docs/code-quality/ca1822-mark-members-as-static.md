---
title: CA1822:メンバーを static に設定します
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 77b256ddaff769263bcc56891ca7c0ad2be30d0c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54979700"
---
# <a name="ca1822-mark-members-as-static"></a>CA1822:メンバーを static に設定します

|||
|-|-|
|TypeName|MarkMembersAsStatic|
|CheckId|CA1822|
|カテゴリ|Microsoft.Performance|
|互換性に影響する変更点|非的なメンバーが、アセンブリの外部に表示されない場合、変更に関係なくすること。 なし - とインスタンス メンバーへのメンバーだけを変更する場合、`this`キーワード。<br /><br /> あり - インスタンスのメンバーから静的メンバーにメンバーを変更して、アセンブリの外側に表示される場合。|

## <a name="cause"></a>原因
 インスタンス データにアクセスしないメンバーが静的とマークされていない (内の共有[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)])。

## <a name="rule-description"></a>規則の説明
 インスタンス データにアクセスしない、またはインスタンス メソッドを呼び出さないメンバーは、静的 ([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では共有) としてマークできます。 メソッドを静的としてマークすると、コンパイラはこれらのメンバーに対する非仮想呼び出しサイトを出力します。 非仮想呼び出しサイトを出力すると、現在のオブジェクト ポインターが null 以外であることを確認する呼び出しごとに実行時のチェックができなくなります。 これは、パフォーマンス重視のコードの測定可能なパフォーマンスの向上を実現できます。 場合によってでは、現在のオブジェクトのインスタンスへのアクセスの失敗は、正確性の問題を表します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 静的メンバーをマーク (で共有したり[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) または 'this' を使用して、/、該当する場合、'Me' メソッドの本文します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 以前にリリース済みのコード修正が重大な変更をすると、この規則からの警告を抑制しても安全です。

## <a name="related-rules"></a>関連するルール
 [CA1811:呼び出されていないプライベート コードを避ける](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812:インスタンス化されていない内部クラスを回避します。](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA 1804:使用されていないローカルを削除します](../code-quality/ca1804-remove-unused-locals.md)