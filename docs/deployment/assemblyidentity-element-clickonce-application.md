---
title: "&lt;assemblyIdentity&gt; 要素 (ClickOnce アプリケーション) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#assemblyIdentity"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<assemblyIdentity> 要素 [ClickOnce アプリケーション マニフェスト]"
ms.assetid: f48e9531-efac-4d11-8166-f63a5ece1ac5
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;assemblyIdentity&gt; 要素 (ClickOnce アプリケーション)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 配置で配置されるアプリケーションを指定します。  
  
## 構文  
  
```  
  
      <assemblyIdentity   
   name  
   version  
   publicKeyToken  
   processorArchitecture  
   language  
/>  
```  
  
## 要素と属性  
 `assemblyIdentity` 要素は必須です。  子要素を含まず、次の属性を持ちます。  
  
|属性|Description|  
|--------|-----------------|  
|`Name`|必ず指定します。  アプリケーションの名前を指定します。<br /><br /> `Name` に単一引用符または二重引用符などの特殊文字が含まれていると、アプリケーションがアクティブ化に失敗する場合があります。|  
|`Version`|必ず指定します。  `major.minor.build.revision` の形式で、アプリケーションのバージョン番号を指定します。|  
|`publicKeyToken`|省略可能です。  アプリケーションまたはアセンブリに署名するために使用する公開キーの `SHA-1` ハッシュ値のうち、最後の 8 バイトを表す 16 文字の 16 進文字列を指定します。  カタログに署名するために使用する公開キーは、2048 ビット以上であることが必要です。<br /><br /> アセンブリへの署名は省略可能ですが、できるだけ実行することをお勧めします。ただし、この属性は必須です。  署名されないアセンブリの場合は、自己署名されたアセンブリから値をコピーするか、すべてをゼロにした "ダミー" の値を使用します。|  
|`processorArchitecture`|必ず指定します。  プロセッサを指定します。  有効な値は、`msil` \(すべてのプロセッサ\)、`x86` \(32 ビット Windows\)、`IA64` \(64 ビット Windows\)、および `Itanium` \(Intel 64 ビット Itanium プロセッサ\) です。|  
|`language`|必ず指定します。  `en-US` のように 2 つの部分から構成されるアセンブリの言語コードを指定します。  この要素は、`asmv2` 名前空間にあります。  既定値は `neutral` です。|  
  
## 例  
  
### Description  
 次のコード例は、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーション マニフェスト内の `assemblyIdentity` 要素を示しています。  このコード例は、「[ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)」で示されている例の一部の抜粋です。  
  
### コード  
  
```  
<asmv1:assemblyIdentity   
  name="My Application Deployment.exe"   
  version="1.0.0.0"   
  publicKeyToken="43cb1e8e7a352766"   
  language="neutral"   
  processorArchitecture="x86"   
  type="win32" />  
```  
  
## 参照  
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)   
 [\<assemblyIdentity\> 要素](../deployment/assemblyidentity-element-clickonce-deployment.md)