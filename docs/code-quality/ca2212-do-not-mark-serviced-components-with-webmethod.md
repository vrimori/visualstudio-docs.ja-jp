---
title: "CA2212: サービス コンポーネントを WebMethod をマークしない |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
helpviewer_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 44c29215301212a12c5652fbf1fe91af23db1082
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
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
 <xref:System.Web.Services.WebMethodAttribute>ASP.NET; を使用して作成された XML Web サービス内のメソッドに適用されます。これにより、メソッド呼び出し可能なリモートの Web クライアントから。 メソッドとクラスは、パブリックにし、ASP.NET Web アプリケーションで実行する必要があります。 <xref:System.EnterpriseServices.ServicedComponent>型は、COM + アプリケーションによってホストされ、COM + サービスを使用することができます。 <xref:System.Web.Services.WebMethodAttribute>適用されません<xref:System.EnterpriseServices.ServicedComponent>同じシナリオに対するものではありません、ために、型です。 具体的には、属性を追加する、<xref:System.EnterpriseServices.ServicedComponent>メソッドは行いませんメソッド呼び出し可能なリモートの Web クライアントからです。 <xref:System.Web.Services.WebMethodAttribute>と<xref:System.EnterpriseServices.ServicedComponent>メソッド競合する動作があり、コンテキストおよびトランザクション フロー、メソッドの動作の要件は一部のシナリオでは不正確になります。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するから属性を削除する、<xref:System.EnterpriseServices.ServicedComponent>メソッドです。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。 これらの要素を組み合わせることが適切であるシナリオはありません。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName>   
 <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>