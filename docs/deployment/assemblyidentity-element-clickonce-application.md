---
title: '&lt;assemblyIdentity&gt;要素 (ClickOnce アプリケーション) |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assemblyIdentity> element [ClickOnce application manifest]
ms.assetid: f48e9531-efac-4d11-8166-f63a5ece1ac5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e70852f0e720f5c7c67fbce82608929ac13728f8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992140"
---
# <a name="ltassemblyidentitygt-element-clickonce-application"></a>&lt;assemblyIdentity&gt;要素 (ClickOnce アプリケーション)
デプロイされたアプリケーションを識別、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]展開します。  
  
## <a name="syntax"></a>構文  
  
```xml
  
      <assemblyIdentity   
   name  
   version  
   publicKeyToken  
   processorArchitecture  
   language  
/>  
```  
  
## <a name="elements-and-attributes"></a>要素と属性  
 `assemblyIdentity`要素が必要です。 子要素が含まれていないと、次の属性があります。  
  
|属性|説明|  
|---------------|-----------------|  
|`Name`|必須です。 アプリケーションの名前を識別します。<br /><br /> 場合`Name`、特殊文字を含む一重または二重の引用符など、アプリケーションがアクティブにできません。|  
|`Version`|必須です。 次の形式で、アプリケーションのバージョン番号を指定します。 `major.minor.build.revision`|  
|`publicKeyToken`|任意。 最後の 8 バイトを表す 16 文字の 16 進文字列を指定します、`SHA-1`アプリケーションまたはアセンブリに署名するとき、公開キーのハッシュ値。 カタログに署名するために使用する公開キーは 2048 ビットである必要がありますまたはそれ以上。<br /><br /> アセンブリへの署名は推奨されますが、省略可能ですが、この属性が必要です。 アセンブリが署名されていない場合は、自己署名されたアセンブリから値をコピーまたはすべてゼロの「ダミー」の値を使用する必要があります。|  
|`processorArchitecture`|必須です。 プロセッサを指定します。 有効な値は`msil`すべてのプロセッサに対して`x86`32 ビットの Windows の`IA64`の 64 ビットの Windows と`Itanium`Intel 64 ビット Itanium プロセッサ用です。|  
|`language`|必須です。 2 部構成の言語コードを識別します (たとえば、 `en-US`) のアセンブリ。 この要素は、`asmv2`名前空間。 指定されていない場合、既定値は`neutral`します。|  
  
## <a name="examples"></a>使用例  
  
### <a name="description"></a>説明  
 次のコード例を示しています、`assemblyIdentity`内の要素を[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション マニフェスト。 このコード例で示されている例の一部は、 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)します。  
  
### <a name="code"></a>コード  
  
```xml  
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
 [\<assemblyIdentity > 要素](../deployment/assemblyidentity-element-clickonce-deployment.md)
