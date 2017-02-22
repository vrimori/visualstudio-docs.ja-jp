---
title: "&lt;dependency&gt; 要素 (ClickOnce アプリケーション) | Microsoft Docs"
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
  - "urn:schemas-microsoft-com:asm.v2#osVersionInfo"
  - "urn:schemas-microsoft-com:asm.v2#os"
  - "http://www.w3.org/2000/09/xmldsig#Transform"
  - "urn:schemas-microsoft-com:asm.v2#dependency"
  - "http://www.w3.org/2000/09/xmldsig#DigestValue"
  - "urn:schemas-microsoft-com:asm.v2#assemblyIdentity"
  - "http://www.w3.org/2000/09/xmldsig#DigestMethod"
  - "http://www.w3.org/2000/09/xmldsig#Transforms"
  - "urn:schemas-microsoft-com:asm.v2#hash"
  - "urn:schemas-microsoft-com:asm.v2#dependentAssembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<dependency> 要素 [ClickOnce アプリケーション マニフェスト]"
  - "マニフェスト [ClickOnce], dependency 要素"
ms.assetid: 09d6a1e0-60f8-4fbd-843b-8e49ee3115a3
caps.latest.revision: 34
caps.handback.revision: 34
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;dependency&gt; 要素 (ClickOnce アプリケーション)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

アプリケーションに必須のプラットフォーム依存関係またはアセンブリ依存関係を識別します。  
  
## 構文  
  
```  
  
      <dependency>  
   <dependentOS  
      supportURL  
      description  
   >  
      <osVersionInfo>  
         <os  
            majorVersion  
            minorVersion  
            buildNumber  
            servicePackMajor  
            servicePackMinor  
            productType  
            suiteType  
         />   
      </osVersionInfo>  
   </dependentOS>  
   <dependentAssembly  
      dependencyType  
      allowDelayedBinding  
      group  
      codeBase  
      size  
   >  
      <assemblyIdentity  
         name  
         version  
         processorArchitecture  
         language  
      >  
         <hash>  
            <dsig:Transforms>  
               <dsig:Transform  
                  Algorithm  
            />  
            </dsig:Transforms>  
            <dsig:DigestMethod />  
            <dsig:DigestValue>  
            </dsig:DigestValue>  
    </hash>  
  
      </assemblyIdentity>  
   </dependentAssembly>  
</dependency>  
```  
  
## 要素と属性  
 `dependency` 要素は必須です。  同じアプリケーション マニフェストに `dependency` のインスタンスが複数存在してもかまいません。  
  
 `dependency` 要素は属性がなく、次の子要素を含みます。  
  
### dependentOS  
 省略可能です。  `osVersionInfo` 要素を含みます。  `dependentOS` 要素と `dependentAssembly` 要素は相互に排他的です。`dependency` 要素にはいずれか一方が必要ですが、両方は指定できません。  
  
 `dependentOS` は、以下の属性をサポートします。  
  
|属性|Description|  
|--------|-----------------|  
|`supportUrl`|省略可能です。  依存関係にあるプラットフォームのサポート URL を指定します。  必要なプラットフォームが見つかると、この URL がユーザーに表示されます。|  
|`description`|省略可能です。  `dependentOS` 要素に記述したオペレーティング システムについて、ユーザーが認識できる形式で記述します。|  
  
### osVersionInfo  
 必ず指定します。  この要素は `dependentOS` 要素の子であり、`os` 要素が含まれています。  この要素に属性はありません。  
  
### os  
 必ず指定します。  この要素は `osVersionInfo` 要素の子です。  この要素には、次の属性があります。  
  
|属性|Description|  
|--------|-----------------|  
|`majorVersion`|必ず指定します。  OS のメジャー バージョン番号を指定します。|  
|`minorVersion`|必ず指定します。  OS のマイナー バージョン番号を指定します。|  
|`buildNumber`|必ず指定します。  OS のビルド番号を指定します。|  
|`servicePackMajor`|必ず指定します。  OS のサービス パックのメジャー番号を指定します。|  
|`servicePackMinor`|省略可能です。  OS のサービス パックのマイナー番号を指定します。|  
|`productType`|省略可能です。  製品の種類を識別します。  有効値は `server`、`workstation`、および `domainController` です。  たとえば、Windows 2000 Professional の場合、この属性は `workstation` です。|  
|`suiteType`|省略可能です。  システムで使用できる製品スイート、またはシステムの構成の種類を識別します。  有効値は、`backoffice`、`blade`、`datacenter`、`enterprise`、`home`、`professional`、`smallbusiness`、`smallbusinessRestricted`、および `terminal` です。  たとえば、Windows 2000 Professional の場合、この属性は `professional` です。|  
  
### dependentAssembly  
 省略可能です。  `assemblyIdentity` 要素を含みます。  `dependentOS` 要素と `dependentAssembly` 要素は相互に排他的です。`dependency` 要素にはいずれか一方が必要ですが、両方は指定できません。  
  
 `dependentAssembly` には、以下の属性があります。  
  
|属性|Description|  
|--------|-----------------|  
|`dependencyType`|必ず指定します。  依存関係の種類を指定します。  有効値は `preprequisite` または `install` です。  `install` アセンブリは、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションの一部としてインストールされます。  `prerequisite` アセンブリは、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションをインストールする前にグローバル アセンブリ キャッシュ \(GAC: Global Assembly Cache\) に存在している必要があります。|  
|`allowDelayedBinding`|必ず指定します。  実行時にアセンブリをプログラムで読み込むことができるかどうかを指定します。|  
|`group`|省略可能です。  `dependencyType` 属性が `install` に設定されている場合は、要求に応じてのみインストールされるアセンブリの名前付きグループを指定します。  詳細については、「[チュートリアル : デザイナーを使用し、ClickOnce 配置 API で必要に応じてアセンブリをダウンロードする](../Topic/Walkthrough:%20Downloading%20Assemblies%20on%20Demand%20with%20the%20ClickOnce%20Deployment%20API%20Using%20the%20Designer.md)」を参照してください。<br /><br /> これが `framework` に設定され、`dependencyType` 属性が `prerequisite` に設定されている場合は、アセンブリを .NET Framework の一部として指定します。  [!INCLUDE[net_v40_short](../debugger/includes/net_v40_short_md.md)] 以降のバージョンにインストールする場合、GAC にこのアセンブリが存在するかどうかはチェックされません。|  
|`codeBase`|`dependencyType` 属性が `install` に設定されている場合には必須です。  依存関係のアセンブリのパスです。  絶対パスまたはマニフェストのコード ベースに対する相対パスで指定します。  アセンブリ マニフェストが有効であるためには、このパスが有効な URI であることが必要です。|  
|`size`|`dependencyType` 属性が `install` に設定されている場合には必須です。  依存関係のアセンブリのサイズ \(バイト単位\) です。|  
  
### assemblyIdentity  
 必ず指定します。  この要素は `dependentAssembly` 要素の子であり、以下の属性があります。  
  
|属性|Description|  
|--------|-----------------|  
|`name`|必ず指定します。  アプリケーションの名前を指定します。|  
|`version`|必ず指定します。  `major.minor.build.revision` の形式で、アプリケーションのバージョン番号を指定します。|  
|`publicKeyToken`|省略可能です。  アプリケーションまたはアセンブリに署名するために使用する公開キーの `SHA-1` ハッシュ値のうち、最後の 8 バイトを表す 16 文字の 16 進文字列を指定します。  カタログに署名するために使用する公開キーは、2048 ビット以上である必要があります。|  
|`processorArchitecture`|省略可能です。  プロセッサを指定します。  有効な値は、32 ビット Windows の場合 `x86`、64 ビット Windows の場合 `I64` です。|  
|`language`|省略可能です。  EN\-US など 2 つの部分から構成されるアセンブリの言語コードを識別します。|  
  
### hash  
 `hash` 要素は、`assemblyIdentity` 要素の子要素で、省略可能です。  `hash` 要素に属性はありません。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] では、セキュリティをチェックするために、アプリケーション内の全ファイルで計算したハッシュを使用して、配置後にどのファイルも変更されていないことを確認できるようにしています。  `hash` 要素が含まれていない場合、このチェックは実行されません。したがって、`hash` 要素を省略することは推奨できません。  
  
### dsig:Transforms  
 `dsig:Transforms` 要素は、`hash` 要素に必須の子です。  `dsig:Transforms` 要素には属性がありません。  
  
### dsig:Transform  
 `dsig:Transform` 要素は、`dsig:Transforms` 要素に必須の子です。  `dsig:Transform` 要素には、次の属性があります。  
  
|属性|Description|  
|--------|-----------------|  
|`Algorithm`|このファイルのダイジェストを計算するために使用するアルゴリズムです。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] が現在使用している唯一の値は、`urn:schemas-microsoft-com:HashTransforms.Identity` です。|  
  
### dsig:DigestMethod  
 `dsig:DigestMethod` 要素は、`hash` 要素に必須の子です。  `dsig:DigestMethod` 要素には、次の属性があります。  
  
|属性|Description|  
|--------|-----------------|  
|`Algorithm`|このファイルのダイジェストを計算するために使用するアルゴリズムです。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] が現在使用している唯一の値は、`http://www.w3.org/2000/09/xmldsig#sha1` です。|  
  
### dsig:DigestValue  
 `dsig:DigestValue` 要素は、`hash` 要素に必須の子です。  `dsig:DigestValue` 要素に属性はありません。  このテキスト値は、指定のファイルで計算されたハッシュです。  
  
## 解説  
 アプリケーションで使用するすべてのアセンブリには、対応する `dependency` 要素が必要です。  プラットフォーム アセンブリとしてグローバル アセンブリ キャッシュにプレインストールする必要のあるアセンブリは、依存関係のアセンブリには含まれません。  
  
## 使用例  
 次のコード例は、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーション マニフェスト内の `dependency` 要素を示しています。  このコード例は、「[ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)」トピックで提供されているより詳細な例の一部です。  
  
```  
<dependency>  
  <dependentOS>  
    <osVersionInfo>  
      <os   
        majorVersion="4"   
        minorVersion="10"   
        buildNumber="0"   
        servicePackMajor="0" />  
    </osVersionInfo>  
  </dependentOS>  
</dependency>  
<dependency>  
  <dependentAssembly  
    dependencyType="preRequisite"  
    allowDelayedBinding="true">  
    <assemblyIdentity  
      name="Microsoft.Windows.CommonLanguageRuntime"  
      version="4.0.20506.0" />  
  </dependentAssembly>  
</dependency>  
  
<dependency>  
  <dependentAssembly  
    dependencyType="install"  
    allowDelayedBinding="true"  
    codebase="MyApplication.exe"  
    size="4096">  
    <assemblyIdentity  
      name="MyApplication"  
      version="1.0.0.0"  
      language="neutral"  
      processorArchitecture="x86" />  
    <hash>  
      <dsig:Transforms>  
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
      </dsig:Transforms>  
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
      <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>  
    </hash>  
  </dependentAssembly>  
</dependency>  
```  
  
## 参照  
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)   
 [\<dependency\> 要素](../deployment/dependency-element-clickonce-deployment.md)