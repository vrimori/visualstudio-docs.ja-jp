---
title: '&lt;assemblyIdentity&gt;要素 (ClickOnce アプリケーション) |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assemblyIdentity> element [ClickOnce application manifest]
ms.assetid: f48e9531-efac-4d11-8166-f63a5ece1ac5
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 67ee803e18a1b098cd8e1bad2befd5a2d794766c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548775"
---
# <a name="ltassemblyidentitygt-element-clickonce-application"></a>&lt;assemblyIdentity&gt;要素 (ClickOnce アプリケーション)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ &lt;assemblyIdentity&gt;要素 (ClickOnce アプリケーション)](https://docs.microsoft.com/visualstudio/deployment/assemblyidentity-element-clickonce-application)します。  
  
デプロイされたアプリケーションを識別、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]展開します。  
  
## <a name="syntax"></a>構文  
  
```  
  
      <assemblyIdentity   
   name  
   version  
   publicKeyToken  
   processorArchitecture  
   language  
/>  
```  
  
## <a name="elements-and-attributes"></a>要素と属性  
 `assemblyIdentity`要素が必要です。 これは、子要素を含まず、かつ、次の属性を持ちます。   
  
|属性|説明|  
|---------------|-----------------|  
|`Name`|必須。 アプリケーションの名前を識別します。<br /><br /> `Name`に、一重引用符または二重引用符のような特殊文字が含まれている場合、アプリケーションはアクティブ化に失敗することがあります。|  
|`Version`|必須。 次の形式で、アプリケーションのバージョン番号を指定します。 `major.minor.build.revision`|  
|`publicKeyToken`|任意。 最後の 8 バイトを表す 16 文字の 16 進文字列を指定します、`SHA-1`アプリケーションまたはアセンブリに署名するとき、公開キーのハッシュ値。 カタログに署名するために使用する公開キーは 2048 ビットである必要がありますまたはそれ以上。<br /><br /> アセンブリの署名は推奨されていますが、任意であり、署名するかに関わらずこの属性は必要です。 アセンブリが署名付きでない場合は、自己署名されたアセンブリから値をコピーするか、すべてがゼロ値である「ダミー」を使用する必要があります。|  
|`processorArchitecture`|必須。 プロセッサを指定します。 有効な値は`msil`すべてのプロセッサに対して`x86`32 ビットの Windows の`IA64`の 64 ビットの Windows と`Itanium`Intel 64 ビット Itanium プロセッサ用です。|  
|`language`|必須。 2 部構成の言語コードを識別します (たとえば、 `en-US`) のアセンブリ。 この要素は、`asmv2`名前空間。 指定されていない場合、既定値は`neutral`します。|  
  
## <a name="examples"></a>使用例  
  
### <a name="description"></a>説明  
 次のコード例は [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]アプリケーション マニフェスト内の `assemblyIdentity` 要素を示しています。 このコード例で示されている例の一部は、 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)します。  
  
### <a name="code"></a>コード  
  
```  
<asmv1:assemblyIdentity   
  name="My Application Deployment.exe"   
  version="1.0.0.0"   
  publicKeyToken="43cb1e8e7a352766"   
  language="neutral"   
  processorArchitecture="x86"   
  type="win32" />  
```  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)   
 [\<assemblyIdentity> 要素](../deployment/assemblyidentity-element-clickonce-deployment.md)



