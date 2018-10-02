---
title: '&lt;署名&gt;要素 (ClickOnce 配置) |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <Signature> element [ClickOnce deployment manifest]
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: b1f829971a1e5a5d62c95c1f81fb75375f7cc74e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47545972"
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>&lt;署名&gt;要素 (ClickOnce 配置)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[&lt;署名&gt;要素 (ClickOnce 配置)](https://docs.microsoft.com/visualstudio/deployment/signature-element-clickonce-deployment)します。  
  
この配置マニフェストにデジタル署名するために必要な情報が含まれます。  
  
## <a name="syntax"></a>構文  
  
```  
  
      <Signature>   
   XML signature information   
</Signature>  
```  
  
## <a name="remarks"></a>Remarks  
 エンベロープ署名を使用して配置マニフェストに署名は省略可能では、お勧めします。 ファイルを XML 署名の詳細については、World Wide Web Consortium 推奨事項、"Xml-signature Syntax and Processing、"」の説明を参照してください[ http://www.w3.org/TR/xmldsig-core/](http://www.w3.org/TR/xmldsig-core/)します。  
  
 マニフェストに署名する場合は、すべてのファイル ハッシュを指定する必要があります。 ユーザーは、ハッシュされていないファイルの内容を確認できないため、ハッシュされていないファイルをマニフェストに署名できません。  
  
## <a name="example"></a>例  
 次のコード例を示しています、`Signature`で使用される配置マニフェスト内の要素を[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]展開します。  
  
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
  
## <a name="see-also"></a>関連項目  
 [ClickOnce 配置マニフェス](../deployment/clickonce-deployment-manifest.md)



