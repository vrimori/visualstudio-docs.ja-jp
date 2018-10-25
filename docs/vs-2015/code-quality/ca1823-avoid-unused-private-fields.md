---
title: ': Ca 1823 使用されていないプライベート フィールド |Microsoft Docs'
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
- AvoidUnusedPrivateFields
- CA1823
helpviewer_keywords:
- AvoidUnusedPrivateFields
- CA1823
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e729bb95f6b36afb4910ac6d03636c239994ae34
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49813493"
---
# <a name="ca1823-avoid-unused-private-fields"></a>CA1823: 使用されていないプライベート フィールドを使用しません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidUnusedPrivateFields|
|CheckId|CA1823|
|カテゴリ|Microsoft.Performance|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 このルールは、コード内のプライベート フィールドが存在しますが、任意のコード パスで使用されていない場合に報告されます。

## <a name="rule-description"></a>規則の説明
 アセンブリ内でアクセスされていないと思われるプライベート フィールドが検出されました。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、フィールドを削除するか、それを使用するコードを追加します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 このルールから警告を抑制しても安全です。

## <a name="related-rules"></a>関連規則
 [CA1812: インスタンス化されていない内部クラスを使用しないでください](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: 使用されていないパラメーターをレビューします](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: 使用されていないローカルを削除します](../code-quality/ca1804-remove-unused-locals.md)

 [CA1811: 呼び出されていないプライベート コードを使用しません](../code-quality/ca1811-avoid-uncalled-private-code.md)



