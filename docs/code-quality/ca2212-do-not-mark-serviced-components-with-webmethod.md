---
title: 'CA2212: サービス コンポーネントを WebMethod をマークしない |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
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
ms.openlocfilehash: ca33b1dfeafa3894b3ad82fd42a04d8310d2bd50
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName>   
 <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>