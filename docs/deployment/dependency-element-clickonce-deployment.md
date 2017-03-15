---
title: "&lt;dependency&gt; 要素 (ClickOnce 配置) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "<dependency> 要素 [ClickOnce 配置マニフェスト]"
ms.assetid: 9b4d2082-0347-4922-ac70-85f11b913039
caps.latest.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 27
---
# &lt;dependency&gt; 要素 (ClickOnce 配置)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

インストールするアプリケーションのバージョンおよびアプリケーション マニフェストの場所を指定します。  
  
## 構文  
  
```  
  
      <dependency>   
   <dependentAssembly  
      preRequisite  
      visible  
      dependencyType  
      codeBase  
      size  
   >   
      <assemblyIdentity   
         name   
         version   
         publicKeyToken   
         processorArchitecture   
         language  
         type  
      />   
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
  
   </dependentAssembly>   
</dependency>  
```  
  
## 要素と属性  
 `dependency` 要素は必須です。  属性はありません。  配置マニフェストは、複数の `dependency` 要素を持つことができます。  
  
 `dependency` 要素では、通常、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションに含まれるメイン アプリケーションのアセンブリに対する依存関係を表します。  Main.exe アプリケーションで DotNetAssembly.dll アセンブリを使用している場合は、このアセンブリを依存関係セクションにリスト アップする必要があります。  また、共通言語ランタイムの特定のバージョンへの依存関係や、グローバル アセンブリ キャッシュ \(GAC: Global Assembly Cache\) にあるアセンブリへの依存関係、COM オブジェクトへの依存関係など、他の種類の依存関係も記述できます。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 配置テクノロジでは、手動による操作は行われないため、このような種類の依存関係をダウンロードしたりインストールしたりすることはできません。ただし、指定した依存対象が存在しない場合に、アプリケーションが実行されないようにすることはできます。  
  
## dependentAssembly  
 必ず指定します。  この要素には、`assemblyIdentity` 要素が含まれています。  `dependentAssembly` でサポートされている属性を次の表に示します。  
  
|属性|Description|  
|--------|-----------------|  
|`preRequisite`|省略可能です。  このアセンブリがあらかじめ GAC に存在している必要があるかどうかを指定します。  有効な値は、`true` および `false` です。  `true` に設定すると、指定したアセンブリが GAC に存在しない場合は、アプリケーションは実行できません。|  
|`visible`|省略可能です。  依存関係を含む、トップレベルのアプリケーション ID を識別します。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 内部で、アプリケーションのストレージおよびアクティベーションを管理するために使用します。|  
|`dependencyType`|必ず指定します。  この依存関係とアプリケーションの間のリレーションシップです。  次の値を指定できます。<br /><br /> -   `Install`:   コンポーネントは、現在のアプリケーションとは個別のインストールを表します。<br />-   `preRequisite`:   コンポーネントは、現在のアプリケーションが必要としています。|  
|`codebase`|省略可能です。  アプリケーション マニフェストの完全パスです。|  
|`size`|省略可能です。  アプリケーション マニフェストのサイズ \(バイト単位\) です。|  
  
## assemblyIdentity  
 必ず指定します。  この要素は `dependentAssembly` 要素の子です。  `assemblyIdentity` の内容は、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーション マニフェストの記述内容と一致している必要があります。  次の表に `assemblyIdentity` 要素の属性を示します。  
  
|属性|Description|  
|--------|-----------------|  
|`Name`|必ず指定します。  アプリケーションの名前を指定します。|  
|`Version`|必ず指定します。  `major.minor.build.revision` の形式で、アプリケーションのバージョン番号を指定します。|  
|`publicKeyToken`|必ず指定します。  アプリケーションまたはアセンブリに署名するために使用する公開キーの SHA\-1 ハッシュ値のうち、最後の 8 バイトを表す 16 文字の 16 進文字列を指定します。  署名するために使用する公開キーは、2048 ビット以上である必要があります。|  
|`processorArchitecture`|必ず指定します。  マイクロプロセッサを指定します。  有効な値は、32 ビット Windows の場合 `x86`、64 ビット Windows の場合 `IA64` です。|  
|`Language`|省略可能です。  2 つの部分で構成されるアセンブリの言語コードを指定します。  たとえば、アメリカ英語の場合 EN\-US です。  既定値は `neutral` です。  この要素は、`asmv2` 名前空間にあります。|  
|`type`|省略可能です。  Windows の side\-by\-side インストール テクノロジとの後方互換性のためにあります。  唯一許容される値は、`win32` です。|  
  
## hash  
 `hash` 要素は、`file` 要素の子要素で、省略可能です。  `hash` 要素に属性はありません。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] では、セキュリティをチェックするために、アプリケーション内の全ファイルで計算したハッシュを使用して、配置後にどのファイルも変更されていないことを確認できるようにしています。  `hash` 要素が含まれていない場合、このチェックは実行されません。したがって、`hash` 要素を省略することは推奨できません。  
  
## dsig:Transforms  
 `dsig:Transforms` 要素は、`hash` 要素に必須の子です。  `dsig:Transforms` 要素には属性がありません。  
  
## dsig:Transform  
 `dsig:Transform` 要素は、`dsig:Transforms` 要素に必須の子です。  `dsig:Transform` 要素の属性を次の表に示します。  
  
|属性|Description|  
|--------|-----------------|  
|`Algorithm`|このファイルのダイジェストを計算するために使用するアルゴリズムです。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] が現在使用している唯一の値は、`urn:schemas-microsoft-com:HashTransforms.Identity` です。|  
  
## dsig:DigestMethod  
 `dsig:DigestMethod` 要素は、`hash` 要素に必須の子です。  `dsig:DigestMethod` 要素の属性を次の表に示します。  
  
|属性|Description|  
|--------|-----------------|  
|`Algorithm`|このファイルのダイジェストを計算するために使用するアルゴリズムです。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] が現在使用している唯一の値は、`http://www.w3.org/2000/09/xmldsig#sha1` です。|  
  
## dsig:DigestValue  
 `dsig:DigestValue` 要素は、`hash` 要素に必須の子です。  `dsig:DigestValue` 要素に属性はありません。  このテキスト値は、指定のファイルで計算されたハッシュです。  
  
## 解説  
 配置マニフェストは通常、アプリケーション マニフェストの名前とバージョンを指定した `assemblyIdentity` 要素を 1 つ持ちます。  
  
## 使用例  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 配置マニフェスト内の `dependency` 要素を次のコード例に示します。  
  
```  
<!-- Identify the assembly dependencies -->  
<dependency>  
  <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="16384">  
    <assemblyIdentity name="MyApplication" version="0.0.0.0" cultural="neutral" processorArchitecture="msil" />  
    <hash>  
      <dsig:Transforms>  
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
      </dsig:Transforms>  
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
       <dsig:DigestValue>YzXYZJAvj9pgAG3y8jXUjC7AtHg=</dsig:DigestValue>  
    </hash>  
  </dependentAssembly>  
</dependency>  
```  
  
## 使用例  
 次のコード例では、既に GAC にインストールされているアセンブリへの依存関係を指定しています。  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="GACAssembly" version="1.0.0.0" language="neutral" processorArchitecture="msil" />  
  </dependentAssembly>  
</dependency>  
```  
  
## 使用例  
 次のコード例では、共通言語ランタイムの特定のバージョンへの依存関係を指定しています。  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50215.0" />  
  </dependentAssembly>  
</dependency>  
```  
  
## 使用例  
 次のコード例では、特定のオペレーティング システムへの依存関係を指定しています。  
  
```  
<dependency>  
   <dependentOS supportUrl="http://www.microsoft.com" description="Microsoft Windows Operating System">  
      <osVersionInfo>  
         <os majorVersion="4" minorVersion="10" />  
      </osVersionInfo>  
   </dependentOS>  
</dependency>  
```  
  
## 参照  
 [ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)   
 [\<dependency\> 要素](../deployment/dependency-element-clickonce-application.md)