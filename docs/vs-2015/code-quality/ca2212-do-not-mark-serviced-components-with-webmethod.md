---
title: ': しない ca 2212 サービス コンポーネントを webmethod に設定 |Microsoft Docs'
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
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
helpviewer_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 33f23ead1a4236c60e8c152f5064d6d1b6f4d3b3
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589616"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: サービス コンポーネントを WebMethod に設定しません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[CA2212: サービス コンポーネントを webmethod に設定をマークしない](https://docs.microsoft.com/visualstudio/code-quality/ca2212-do-not-mark-serviced-components-with-webmethod)します。

|||
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 継承する型のメソッド<xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName>でマークされた<xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>します。

## <a name="rule-description"></a>規則の説明
 <xref:System.Web.Services.WebMethodAttribute> ASP.NET; を使用して作成された XML Web サービス内のメソッドに適用されます。それにより、リモートの Web クライアントからメソッドを呼び出し可能にします。 メソッドとクラスは、パブリックにし、ASP.NET Web アプリケーションで実行する必要があります。 <xref:System.EnterpriseServices.ServicedComponent> 種類は、COM + アプリケーションでホストされており、COM + サービスを使用することができます。 <xref:System.Web.Services.WebMethodAttribute> 適用されません<xref:System.EnterpriseServices.ServicedComponent>型同じシナリオに対する意図されていないためです。 具体的には、属性を追加する、<xref:System.EnterpriseServices.ServicedComponent>メソッドを行わない、メソッド呼び出し可能なリモートの Web クライアントから。 <xref:System.Web.Services.WebMethodAttribute>と<xref:System.EnterpriseServices.ServicedComponent>メソッドがある動作が競合して、コンテキストとトランザクション フロー、メソッドの動作の要件は一部のシナリオでは不正確になります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を解決するからの属性を削除、<xref:System.EnterpriseServices.ServicedComponent>メソッド。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。 これらの要素を組み合わせることが適切であるシナリオではありません。

## <a name="see-also"></a>関連項目
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>



