---
title: "&lt;assemblyIdentity&gt;要素 (ClickOnce アプリケーション) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: b731522897512300459a32f8e01c4d54277eaa5b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltassemblyidentitygt-element-clickonce-application"></a>&lt;assemblyIdentity&gt;要素 (ClickOnce アプリケーション)
展開されているアプリケーションを識別、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]展開します。  
  
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
 `assemblyIdentity`要素が必要です。 これは、子要素が含まれていない、次の属性です。  
  
|属性|説明|  
|---------------|-----------------|  
|`Name`|必須。 アプリケーションの名前を識別します。<br /><br /> 場合`Name`の特殊文字が含まれています、一重引用符または二重引用符など、アプリケーションがアクティブ化に失敗可能性があります。|  
|`Version`|必須。 次の形式で、アプリケーションのバージョン番号を指定します。`major.minor.build.revision`|  
|`publicKeyToken`|任意。 最後の 8 バイトを表す 16 文字の 16 進文字列を指定、`SHA-1`アプリケーションまたはアセンブリが署名に使用された公開キーのハッシュ値。 カタログに署名するために使用する公開キーは 2048 ビットである必要がありますか値を超えています。<br /><br /> アセンブリに署名する推奨であり、省略可能なこの属性が必要です。 アセンブリが署名付きでない場合は、自己署名されたアセンブリから値をコピーするか、「ダミー」値がすべてゼロを使用する必要があります。|  
|`processorArchitecture`|必須。 プロセッサを指定します。 有効な値は`msil`すべてのプロセッサに対して`x86`32 ビット Windows の`IA64`64 ビット windows の場合と`Itanium`Intel 64 ビット Itanium プロセッサ用です。|  
|`language`|必須。 2 部構成の言語コードを識別する (たとえば、 `en-US`) アセンブリのです。 この要素は、`asmv2`名前空間。 値を指定しない場合、既定値は`neutral`します。|  
  
## <a name="examples"></a>使用例  
  
### <a name="description"></a>説明  
 次のコード例を示しています、`assemblyIdentity`内の要素、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション マニフェスト。 このコード例に示されている例の一部である[ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)です。  
  
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
  
## <a name="see-also"></a>参照  
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)   
 [\<assemblyIdentity > 要素](../deployment/assemblyidentity-element-clickonce-deployment.md)