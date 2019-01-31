---
title: '&lt;assemblyIdentity&gt;要素 (ClickOnce 配置) |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assemblyIdentity> element [ClickOnce deployment manifest]
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2ebe08584e3be85b38778276c7876a6394d2cef1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55043155"
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;assemblyIdentity&gt;要素 (ClickOnce 配置)
プライマリ アセンブリを識別、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
      <assemblyIdentity    
   name   
   version  
   publicKeyToken  
   processorArchitecture  
    type  
/>  
```  
  
## <a name="elements-and-attributes"></a>要素と属性  
 `assemblyIdentity`要素が必要です。 子要素が含まれていないと、次の属性があります。  
  
|属性|説明|  
|---------------|-----------------|  
|`name`|必須です。 情報提供を目的の配置の人間が判読できる名前を識別します。<br /><br /> 場合`name`、特殊文字を含む一重または二重の引用符など、アプリケーションがアクティブにできません。|  
|`version`|必須です。 次の形式で、アセンブリのバージョン番号を指定します:`major.minor.build.revision`します。<br /><br /> この値は、アプリケーションの更新をトリガーする、更新したマニフェストを増加する必要があります。|  
|`publicKeyToken`|必須です。 配置マニフェストに署名するとき、公開キーの sha-1 ハッシュ値の最後の 8 バイトを表す 16 文字の 16 進文字列を指定します。 サインインに使用される公開キーは 2048 ビットである必要がありますまたはそれ以上。<br /><br /> アセンブリへの署名は推奨されますが、省略可能ですが、この属性が必要です。 アセンブリが署名されていない場合は、自己署名されたアセンブリから値をコピーまたはすべてゼロの「ダミー」の値を使用する必要があります。|  
|`processorArchitecture`|必須です。 プロセッサを指定します。 有効な値は`msil`すべてのプロセッサに対して`x86`32 ビットの Windows の`IA64`の 64 ビットの Windows と`Itanium`Intel 64 ビット Itanium プロセッサ用です。|  
|`type`|必須です。 Windows サイド バイ サイドでインストール テクノロジとの互換性。 唯一の許容値は`win32`します。|  
  
## <a name="remarks"></a>コメント  
  
## <a name="example"></a>例  
 次のコード例を示しています、`assemblyIdentity`内の要素を[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]配置マニフェスト。 このコード例が示されている例の一部、 [ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)トピック。  
  
```xml  
<!-- Identify the deployment. -->  
<assemblyIdentity   
  name="My Application Deployment.app"  
  version="1.0.0.0"  
  publicKeyToken="43cb1e8e7a352766"  
  language="neutral"  
  processorArchitecture="x86"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)   
 [\<assemblyIdentity > 要素](../deployment/assemblyidentity-element-clickonce-application.md)