---
title: "CA2212: サービス コンポーネントを WebMethod に設定しません | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2212"
  - "DoNotMarkServicedComponentsWithWebMethod"
helpviewer_keywords: 
  - "CA2212"
  - "DoNotMarkServicedComponentsWithWebMethod"
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2212: サービス コンポーネントを WebMethod に設定しません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotMarkServicedComponentsWithWebMethod|  
|CheckId|CA2212|  
|分類|Microsoft.Usage|  
|互換性に影響する変更点|あり|  
  
## 原因  
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> から継承された型のメソッドが、<xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName> でマークされています。  
  
## 規則の説明  
 <xref:System.Web.Services.WebMethodAttribute> は、ASP.NET を使用して作成された XML Web サービス内のメソッドに適用されます。これによって、メソッドをリモートの Web クライアントから呼び出すことができるようになります。  メソッドとクラスはパブリックにし、ASP.NET Web アプリケーションで実行する必要があります。  <xref:System.EnterpriseServices.ServicedComponent> 型は、COM\+ アプリケーションでホストされ、COM\+ サービスを使用できます。  <xref:System.Web.Services.WebMethodAttribute> は <xref:System.EnterpriseServices.ServicedComponent> 型に適用されません。これは用途が異なるためです。  特に、<xref:System.EnterpriseServices.ServicedComponent> メソッドにこの属性を追加しても、リモートの Web クライアントからメソッドを呼び出すことができない点が異なります。  <xref:System.Web.Services.WebMethodAttribute> と <xref:System.EnterpriseServices.ServicedComponent> メソッドは、コンテキストおよびトランザクション フローの動作および要件が衝突するため、状況によってこのメソッドは正常に動作しません。  
  
## 違反の修正方法  
 この規則違反を修正するには、<xref:System.EnterpriseServices.ServicedComponent> メソッドからこの属性を削除します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  これらの要素を結合する処理が適切な場合はありません。  
  
## 参照  
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName>   
 <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>