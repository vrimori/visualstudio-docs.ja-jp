---
title: "Ca 1059: メンバーは特定の具象型を公開できません |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1059
- MembersShouldNotExposeCertainConcreteTypes
helpviewer_keywords:
- MembersShouldNotExposeCertainConcreteTypes
- CA1059
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: eae9070d76312fa4840f2cf8724a74a2cde4f7b2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca1059-members-should-not-expose-certain-concrete-types"></a>CA1059: メンバーは特定の具象型を公開できません
|||  
|-|-|  
|TypeName|MembersShouldNotExposeCertainConcreteTypes|  
|CheckId|CA1059|  
|カテゴリ|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 外部から参照できるメンバーは、特定の具象型は、またはそのパラメーターのいずれかで特定の具象型を公開または戻り値。 現時点では、このルールは、次の具体的な種類の公開をレポートします。  
  
-   派生した型<xref:System.Xml.XmlNode?displayProperty=fullName>です。  
  
## <a name="rule-description"></a>規則の説明  
 具象型は、完全な実装を含む型であるため、インスタンス化できます。 メンバーを広範囲に使用を許可するのには、具象型に推奨のインターフェイスを置き換えます。 これにより、インターフェイスを実装する任意の型を受け入れるか、インターフェイスを実装する型が必要な場所を使用するメンバー。  
  
 次の表には、対象となる具象型とその推奨される代替が一覧表示します。  
  
|具象型|Replacement|  
|-------------------|-----------------|  
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>。<br /><br /> インターフェイスを使用して、XML データ ソースの特定の実装からメンバーを切り離します。|  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、推奨のインターフェイスに具象型を変更します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 これは具象型で提供される特定の機能が必要な場合は、この規則からのメッセージを抑制しても安全です。  
  
## <a name="related-rules"></a>関連規則  
 [CA1011: 基本型をパラメーターとして渡すことを考慮します](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)