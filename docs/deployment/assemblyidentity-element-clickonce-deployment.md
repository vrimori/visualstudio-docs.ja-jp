---
title: '&lt;assemblyIdentity&gt;要素 (ClickOnce 配置) |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51ee3ae65c107fc3e6fafbacc3b2e20652ae998d
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078028"
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;assemblyIdentity&gt;要素 (ClickOnce 配置)
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションのプライマリ アセンブリを識別します。  
  
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
 `assemblyIdentity`要素が必要です。 これは、子要素を含まず、かつ、次の属性を持ちます。   
  
|属性|説明|  
|---------------|-----------------|  
|`name`|必須。 情報提供を目的として、人間が判読できる配置の名前を指定します。<br /><br /> `name`に、一重引用符または二重引用符のような特殊文字が含まれている場合、アプリケーションはアクティブ化に失敗することがあります。|  
|`version`|必須。 アセンブリのバージョン番号を次の形式で指定します:`major.minor.build.revision`.<br /><br /> この値は、アプリケーションの更新をトリガーするマニフェストが更新されるたび、増加する必要があります。|  
|`publicKeyToken`|必須。 配置マニフェストに署名する公開キーの sha-1 ハッシュ値の最後の 8 バイトを表す 16 文字の 16 進文字列を指定します。 署名に使用する公開キーは 2048 ビット以上である必要があります。<br /><br /> アセンブリの署名は推奨されていますが、任意であり、署名するかに関わらずこの属性は必要です。 アセンブリが署名付きでない場合は、自己署名されたアセンブリから値をコピーするか、すべてがゼロ値である「ダミー」を使用する必要があります。|  
|`processorArchitecture`|必須。 プロセッサを指定します。 有効な値は`msil`すべてのプロセッサに対して`x86`32 ビットの Windows の`IA64`の 64 ビットの Windows と`Itanium`Intel 64 ビット Itanium プロセッサ用です。|  
|`type`|必須。 Windows サイド バイ サイド インストール テクノロジとの互換性を維持します。 許可されている値は`win32`だけです。 唯一の許容値は`win32`します。|  
  
## <a name="remarks"></a>Remarks  
  
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