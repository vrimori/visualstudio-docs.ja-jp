---
title: '&lt;署名&gt;要素 (ClickOnce 配置) |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <Signature> element [ClickOnce deployment manifest]
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: cae29bf7f1d5207258ddc90e7287f7fb3a3b2989
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>&lt;署名&gt;要素 (ClickOnce 配置)
この配置マニフェストにデジタル署名するために必要な情報が含まれます。  
  
## <a name="syntax"></a>構文  
  
```  
  
      <Signature>   
   XML signature information   
</Signature>  
```  
  
## <a name="remarks"></a>コメント  
 エンベロープ署名を使用して配置マニフェストに署名オプションですが、ことをお勧めします。 ファイルを XML 署名の詳細については、World Wide Web Consortium 推奨事項を「XML 署名の構文と処理を」」の説明を参照してください[ http://www.w3.org/TR/xmldsig-core/](http://www.w3.org/TR/xmldsig-core/)です。  
  
 マニフェストに署名する場合は、すべてのファイル ハッシュを指定する必要があります。 ユーザーは、ハッシュされていないファイルの内容を確認できないため、ハッシュされていないファイルを含むマニフェストは署名できません。  
  
## <a name="example"></a>例  
 次のコード例を示しています、`Signature`で使用されている配置マニフェスト内の要素、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]展開します。  
  
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