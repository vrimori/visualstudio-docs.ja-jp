---
title: 'CA2212: サービス コンポーネントを WebMethod に設定しません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
helpviewer_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 67d2e2790db4a3e8061dcd949b79c127e67f022d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: サービス コンポーネントを WebMethod に設定しません
|||
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 継承する型のメソッド<xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName>でマークされた<xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>です。

## <a name="rule-description"></a>規則の説明
 <xref:System.Web.Services.WebMethodAttribute> ASP.NET; を使用して作成された XML Web サービス内のメソッドに適用されます。これにより、メソッド呼び出し可能なリモートの Web クライアントから。 メソッドとクラスは、パブリックにし、ASP.NET Web アプリケーションで実行する必要があります。 <xref:System.EnterpriseServices.ServicedComponent> 型は、COM + アプリケーションによってホストされ、COM + サービスを使用することができます。 <xref:System.Web.Services.WebMethodAttribute> 適用されません<xref:System.EnterpriseServices.ServicedComponent>同じシナリオに対するものではありません、ために、型です。 具体的には、属性を追加する、<xref:System.EnterpriseServices.ServicedComponent>メソッドは行いませんメソッド呼び出し可能なリモートの Web クライアントからです。 <xref:System.Web.Services.WebMethodAttribute>と<xref:System.EnterpriseServices.ServicedComponent>メソッド競合する動作があり、コンテキストおよびトランザクション フロー、メソッドの動作の要件は一部のシナリオでは不正確になります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するから属性を削除する、<xref:System.EnterpriseServices.ServicedComponent>メソッドです。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。 これらの要素を組み合わせることが適切であるシナリオはありません。

## <a name="see-also"></a>関連項目
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>