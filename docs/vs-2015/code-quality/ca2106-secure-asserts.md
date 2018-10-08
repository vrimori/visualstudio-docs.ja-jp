---
title: 'Ca 2106: セキュリティで保護されたアサート |Microsoft Docs'
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
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 67d1228b7684b2ba00a7e64f3755fb107fa0e75b
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591878"
---
# <a name="ca2106-secure-asserts"></a>CA2106: アサートをセキュリティで保護します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ca 2106: アサートをセキュリティで保護された](https://docs.microsoft.com/visualstudio/code-quality/ca2106-secure-asserts)します。

|||
|-|-|
|TypeName|SecureAsserts|
|CheckId|CA2106|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 メソッドによってアクセス許可がアサートされますが、呼び出し元に対してセキュリティ チェックが実行されていません。

## <a name="rule-description"></a>規則の説明
 セキュリティ チェックを実行せずにセキュリティ アクセス許可をアサートすると、悪用される可能性があるセキュリティの弱点がコード内に残る場合があります。 セキュリティ アクセス許可がアサートされたときに、セキュリティのスタック ウォークが停止します。 呼び出し元のすべてのチェックを実行せずにアクセス許可をアサートする場合、呼び出し元直接コードを実行しない、アクセス許可を使用します。 セキュリティ チェックは有害な方法で、アサートを使用することはできませんがわかっている場合のみで許容されるせずにアサートします。 アサートが害のないを呼び出すコードは、無害な場合や、ユーザーが任意の情報を呼び出したコードに渡すことはできません。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、メソッド、またはその宣言型セキュリティ確認要求を追加します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 注意が必要なセキュリティ レビュー後にのみこの規則による警告を抑制します。

## <a name="see-also"></a>関連項目
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> [安全なコーディングのガイドライン](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)



