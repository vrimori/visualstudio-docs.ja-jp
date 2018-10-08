---
title: 'Ca 1059: メンバーは特定の具象型を公開しない |Microsoft Docs'
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
- CA1059
- MembersShouldNotExposeCertainConcreteTypes
helpviewer_keywords:
- MembersShouldNotExposeCertainConcreteTypes
- CA1059
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 073d55a9a5ae6caa573a2c3db282aaa5e5ea4e57
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591982"
---
# <a name="ca1059-members-should-not-expose-certain-concrete-types"></a>CA1059: メンバーは特定の具象型を公開できません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ca 1059: メンバーは、特定の具象型を公開できません](https://docs.microsoft.com/visualstudio/code-quality/ca1059-members-should-not-expose-certain-concrete-types)します。

|||
|-|-|
|TypeName|MembersShouldNotExposeCertainConcreteTypes|
|CheckId|CA1059|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 外部から参照は、特定の具象型は、またはそのパラメーターのいずれかで特定の具象型を公開または戻り値。 現在、このルールは、次の具体的な種類の公開を報告します。

-   派生した型<xref:System.Xml.XmlNode?displayProperty=fullName>します。

## <a name="rule-description"></a>規則の説明
 具象型は、完全な実装を含む型であるため、インスタンス化できます。 メンバーの広範囲な使用を許可するのには、推奨のインターフェイスで具象型を置き換えます。 これにより、インターフェイスを実装する任意の型を受け入れるか、インターフェイスを実装する型が必要な場合に使用するメンバー。

 次の表には、対象の具体的な型とその推奨される代替が一覧表示します。

|具象型|Replacement|
|-------------------|-----------------|
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>。<br /><br /> XML データ ソースの特定の実装からメンバーを分離するインターフェイスを使用します。|

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、推奨されるインターフェイスを具象型を変更します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 具体的な型によって提供される特定の機能が必要な場合は、この規則からのメッセージを抑制するのには安全です。

## <a name="related-rules"></a>関連規則
 [CA1011: 基本型をパラメーターとして渡すことを考慮します](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)



