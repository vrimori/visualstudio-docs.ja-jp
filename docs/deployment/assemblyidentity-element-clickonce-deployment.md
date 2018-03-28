---
title: '&lt;assemblyIdentity&gt;要素 (ClickOnce 配置) |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
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
- <assemblyIdentity> element [ClickOnce deployment manifest]
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
caps.latest.revision: ''
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 51643b8db91c9f8c2961b319d47cdfb7789f6a4d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;assemblyIdentity&gt;要素 (ClickOnce 配置)
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションのプライマリ アセンブリを識別します。   
  
## <a name="syntax"></a>構文  
  
```  
  
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
|`name`|必須。 情報提供を目的の配置の人間が判読できる名前を指定します。<br /><br /> 場合`name`の特殊文字が含まれています、一重引用符または二重引用符など、アプリケーションがアクティブ化に失敗可能性があります。|  
|`version`|必須。 アセンブリのバージョン番号を次の形式で指定します:`major.minor.build.revision`.<br /><br /> この値は、アプリケーションの更新をトリガーするマニフェストが更新されるたび、増加する必要があります。|  
|`publicKeyToken`|必須。 配置マニフェストに署名する公開キーの sha-1 ハッシュ値の最後の 8 バイトを表す 16 文字の 16 進文字列を指定します。 署名に使用する公開キーは 2048 ビット以上である必要があります。<br /><br /> アセンブリの署名は推奨されていますが、任意であり、署名するかに関わらずこの属性は必要です。 アセンブリが署名付きでない場合は、自己署名されたアセンブリから値をコピーするか、すべてがゼロ値である「ダミー」を使用する必要があります。|  
|`processorArchitecture`|必須。 プロセッサを指定します。 有効な値は`msil`すべてのプロセッサに対して`x86`32 ビット Windows の`IA64`64 ビット windows 用の`Itanium`そして Intel 64 ビット Itanium プロセッサ用の`Itanium`です。|  
|`type`|必須。 Windows サイド バイ サイド インストール テクノロジとの互換性を維持します。 許可されている値は`win32`だけです。 許可されている値だけ`win32`です。|  
  
## <a name="remarks"></a>コメント  
  
## <a name="example"></a>例  
 次のコード例を示しています、`assemblyIdentity`内の要素、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]配置マニフェスト。 このコード例に示されている例の一部である、 [ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)トピックです。  
  
```  
<!-- Identify the deployment. -->  
<assemblyIdentity   
  name="My Application Deployment.app"  
  version="1.0.0.0"  
  publicKeyToken="43cb1e8e7a352766"  
  language="neutral"  
  processorArchitecture="x86"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>参照  
 [ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)   
 [\<assemblyIdentity > 要素が必要です。](../deployment/assemblyidentity-element-clickonce-application.md)