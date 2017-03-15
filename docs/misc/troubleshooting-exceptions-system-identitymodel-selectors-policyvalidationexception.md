---
title: "例外のトラブルシューティング : System.IdentityModel.Selectors.PolicyValidationException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "PolicyValidationException 例外"
  - "System.IdentityModel.Selectors.PolicyValidationException 例外"
ms.assetid: 510c7698-a12b-4bcb-a9d8-87c704b62ffa
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.IdentityModel.Selectors.PolicyValidationException
<xref:System.IdentityModel.Selectors.PolicyValidationException> 例外は、受信者によって指定されたポリシーを検証できない場合にスローされます。 ポリシーの要件の詳細については、「[A Technical Reference for the Information Card Profile V1.0](http://go.microsoft.com/fwlink/?LinkID=102401)」を参照してください。  
  
 ポリシーに無効なコンテンツがあると、このエラーが発生する可能性があります。 ポリシー コンテンツに関する一般的な問題は、次のとおりです。  
  
-   無効なキーの種類  
  
-   無効なキー サイズ  
  
-   無効な XML  
  
-   ポリシー内に Claim が指定されていない \(必須の Claim を少なくとも 1 つ指定する必要があります\)  
  
## 参照  
 <xref:System.IdentityModel.Selectors.PolicyValidationException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)