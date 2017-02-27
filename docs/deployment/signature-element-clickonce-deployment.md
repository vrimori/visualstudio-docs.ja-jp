---
title: "&lt;Signature&gt; 要素 (ClickOnce 配置) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<Signature> 要素 [ClickOnce 配置マニフェスト]"
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# &lt;Signature&gt; 要素 (ClickOnce 配置)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この配置マニフェストにデジタル署名するために必要な情報を格納します。  
  
## 構文  
  
```  
  
      <Signature>   
   XML signature information   
</Signature>  
```  
  
## 解説  
 エンベロープ シグネチャを使用した配置マニフェストへの署名は省略可能ですが、できるだけ実行することをお勧めします。  XML ファイルへの署名の詳細については、[http:\/\/www.w3.org\/TR\/xmldsig\-core\/](http://www.w3.org/TR/xmldsig-core/) にある W3C \(World Wide Web Consortium\) の勧告「XML\-Signature Syntax and Processing」を参照してください。  
  
 マニフェストに署名する場合は、すべてのファイルに対してハッシュを生成する必要があります。  ハッシュされていないファイルを含むマニフェストには署名できません。これは、ハッシュされていないファイルのコンテンツをユーザーが確認できないためです。  
  
## 使用例  
 次のコード例は、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] で使用される配置マニフェスト内の `Signature` 要素を示しています。  
  
```  
<Signature xmlns="http://www.w3.org/2000/09/xmldsig#">  
  <SignedInfo>  
    <CanonicalizationMethod Algorithm=  
           "http://www.w3.org/TR/2001/REC-xml-c14n-20010315" />  
    <SignatureMethod Algorithm=  
           "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />  
    <Reference URI="">  
      <Transforms>  
        <Transform Algorithm=  
           "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />  
      </Transforms>  
      <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
      <DigestValue>d2z5AE...</DigestValue>  
    </Reference>  
  </SignedInfo>  
  <SignatureValue>  
4PHj6SaopoLp...  
  </SignatureValue>  
  <KeyInfo>  
    <X509Data>  
      <X509Certificate>  
MIIHnTCCBoWgAwIBAgIKJY9+nwAHAAB...  
      </X509Certificate>  
    </X509Data>  
  </KeyInfo>  
</Signature>  
```  
  
## 参照  
 [ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)