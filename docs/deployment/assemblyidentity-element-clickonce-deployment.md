---
title: "&lt;assemblyIdentity&gt; 要素 (ClickOnce 配置) | Microsoft Docs"
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
  - "<assemblyIdentity> 要素 [ClickOnce 配置マニフェスト]"
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;assemblyIdentity&gt; 要素 (ClickOnce 配置)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションのプライマリ アセンブリを指定します。  
  
## 構文  
  
```  
  
      <assemblyIdentity    
   name   
   version  
   publicKeyToken  
   processorArchitecture  
    type  
/>  
```  
  
## 要素と属性  
 `assemblyIdentity` 要素は必須です。  子要素を含まず、次の属性を持ちます。  
  
|属性|Description|  
|--------|-----------------|  
|`name`|必ず指定します。  配置の名前を情報として表示するために、ユーザーが認識できる形式で指定します。<br /><br /> `name` に単一引用符または二重引用符などの特殊文字が含まれていると、アプリケーションがアクティブ化に失敗する場合があります。|  
|`version`|必ず指定します。  `major.minor.build.revision` の形式で、アセンブリのバージョン番号を指定します。<br /><br /> この値は、アプリケーションの更新がトリガーされるように、更新したマニフェストで増やす必要があります。|  
|`publicKeyToken`|必ず指定します。  配置マニフェストに署名するために使用した公開キーの SHA\-1 ハッシュ値のうち、最後の 8 バイトを表す 16 文字の 16 進文字列を指定します。  署名に使用する公開キーは、2048 ビット以上であることが必要です。<br /><br /> アセンブリへの署名は省略可能ですが、できるだけ実行することをお勧めします。ただし、この属性は必須です。  署名されないアセンブリの場合は、自己署名されたアセンブリから値をコピーするか、すべてをゼロにした "ダミー" の値を使用します。|  
|`processorArchitecture`|必ず指定します。  プロセッサを指定します。  有効な値は、`msil` \(すべてのプロセッサ\)、`x86` \(32 ビット Windows\)、`IA64` \(64 ビット Windows\)、および `Itanium` \(Intel 64 ビット Itanium プロセッサ\) です。|  
|`type`|必ず指定します。  Windows の side\-by\-side インストール テクノロジとの互換性のためにあります。  唯一許容される値は、`win32` です。|  
  
## 解説  
  
## 使用例  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 配置マニフェスト内の `assemblyIdentity` 要素を次のコード例に示します。  このコード例は、「[ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)」で紹介されている大きな例の一部です。  
  
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
  
## 参照  
 [ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)   
 [\<assemblyIdentity\> 要素](../deployment/assemblyidentity-element-clickonce-application.md)