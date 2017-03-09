---
title: "例外のトラブルシューティング : System.IdentityModel.Selectors.UnsupportedPolicyOptionsException | Microsoft Docs"
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
  - "System.IdentityModel.Selectors.UnsupportedPolicyOptionsException 例外"
  - "UnsupportedPolicyOptionsException 例外"
ms.assetid: 1151127d-81a1-4d87-8462-924ab9d1ee01
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.IdentityModel.Selectors.UnsupportedPolicyOptionsException
<xref:System.IdentityModel.Selectors.UnsupportedPolicyOptionsException> 例外は、サポートされないオプションを含むシステムに対してポリシーが指定されたことを示します。 これらのエラーが発生するのは次の場合です。  
  
 受信者が、トークンの発行者として http:\/\/schemas.xmlsoap.org\/ws\/2005\/05\/identity\/issuer\/self を指定して、ローカル セキュリティ トークン サービスのトークンを要求しました。 しかし、ポリシーで指定されている要件のいずれかが、CardSpace ローカル セキュリティ トークン サービスでサポートされていません。 詳細については、「[A Technical Reference for the Information Card Profile V1.0](http://go.microsoft.com/fwlink/?LinkId=102401)」を参照してください。 サポートされていないオプションの例を次に示します。  
  
-   受信者によって要求された Claim が、「A Technical Reference for the Information Card Profile V1.0」の「[Supported Claim Types](http://go.microsoft.com/fwlink/?LinkId=102402)」に示されている、サポートされる Claim の一覧にありません。  
  
-   トークンの種類が SAML 1.0 または 1.1 以外です。  
  
-   非 SSL サイトの場合、キーが非対称です。  
  
-   KeyWrapAlgorithm が、既定のアルゴリズムとは異なります。  
  
-   サポートされていない要素が、ポリシーに指定されています。 サポートされている要素は、次のとおりです。  
  
    -   EncryptionAlgorithm  
  
    -   CanonicalizationAlgorithm  
  
    -   SignWith  
  
    -   TokenType  
  
    -   ClaimsElement  
  
    -   KeyType  
  
    -   KeySize  
  
    -   EncryptWith  
  
    -   RequestType  
  
    -   SecondaryParameters  
  
    -   KeyWrapAlgorithm  
  
-   wst:RequestType が Issue 型ではありません。  
  
-   非対称キーの場合、キー サイズが 2048 ではありません。  
  
## 参照  
 <xref:System.IdentityModel.Selectors.UnsupportedPolicyOptionsException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)