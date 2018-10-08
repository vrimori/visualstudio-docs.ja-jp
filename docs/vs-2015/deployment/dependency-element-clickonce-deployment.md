---
title: '&lt;依存関係&gt;要素 (ClickOnce 配置) |Microsoft Docs'
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
- urn:schemas-microsoft-com:asm.v2#osVersionInfo
- urn:schemas-microsoft-com:asm.v2#os
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#dependency
- http://www.w3.org/2000/09/xmldsig#DigestValue
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
- urn:schemas-microsoft-com:asm.v2#dependentAssembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <dependency> element [ClickOnce deployment manifest]
ms.assetid: 9b4d2082-0347-4922-ac70-85f11b913039
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 735b37196586f540186a3ca43c9c315ede51d084
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539422"
---
# <a name="ltdependencygt-element-clickonce-deployment"></a>&lt;依存関係&gt;要素 (ClickOnce 配置)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[&lt;依存関係&gt;要素 (ClickOnce 配置)](https://docs.microsoft.com/visualstudio/deployment/dependency-element-clickonce-deployment)します。  
  
をインストールするアプリケーションのバージョンとアプリケーション マニフェストの場所を識別します。  
  
## <a name="syntax"></a>構文  
  
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
  
## <a name="elements-and-attributes"></a>要素と属性  
 `dependency`要素が必要です。 属性ではありません。 配置マニフェストでは複数`dependency`要素。  
  
 `dependency`要素は通常内に含まれるアセンブリでメイン アプリケーションの依存関係を表現する[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]アプリケーション。 Main.exe アプリケーションでは、DotNetAssembly.dll という名前のアセンブリを消費する場合、依存関係セクションではそのアセンブリを表示する必要があります。 依存関係、ただし、表すことも他の種類など、共通言語ランタイムの特定のバージョンに依存関係の依存関係のグローバル アセンブリ キャッシュ (GAC) 内のアセンブリまたは COM オブジェクト。 ノータッチ デプロイメントのテクノロジである[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]防ぐことはできません、依存関係が、この種の開始のダウンロードとインストールは、アプリケーションの実行、指定した依存関係の 1 つ以上が存在しない場合。  
  
## <a name="dependentassembly"></a>dependentAssembly  
 必須。 この要素が含まれています、`assemblyIdentity`要素。 次の表は、属性、`dependentAssembly`をサポートしています。  
  
|属性|説明|  
|---------------|-----------------|  
|`preRequisite`|任意。 このアセンブリが GAC に既に存在する必要があるを指定します。 有効値は `true` または `false` です。 場合`true`を実行するアプリケーションが失敗した、指定したアセンブリが GAC に存在しません。|  
|`visible`|任意。 依存関係を含む、最上位のアプリケーション id を識別します。 によって内部的に使用される[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]アプリケーション記憶域とアクティブ化を管理します。|  
|`dependencyType`|必須。 この依存関係とアプリケーション間のリレーションシップ。 次の値を指定できます。<br /><br /> -   `install`. コンポーネントは、現在のアプリケーションから別のインストールを表します。<br />-   `preRequisite`. コンポーネントは、現在のアプリケーションで必要です。|  
|`codebase`|任意。 アプリケーション マニフェストの完全パスです。|  
|`size`|任意。 (バイト単位)、アプリケーション マニフェストのサイズ。|  
  
## <a name="assemblyidentity"></a>assemblyIdentity  
 必須。 この要素は `dependentAssembly` 要素の子です。 コンテンツ`assemblyIdentity`で説明されているものと同じである必要があります、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]アプリケーション マニフェスト。 次の表の属性を示します、`assemblyIdentity`要素。  
  
|属性|説明|  
|---------------|-----------------|  
|`Name`|必須。 アプリケーションの名前を識別します。|  
|`Version`|必須。 次の形式で、アプリケーションのバージョン番号を指定します。 `major.minor.build.revision`|  
|`publicKeyToken`|必須。 アプリケーションまたはアセンブリに署名するとき、公開キーの sha-1 ハッシュの最後の 8 バイトを表す 16 文字の 16 進文字列を指定します。 署名に使用される公開キーは 2048 ビットである必要がありますまたはそれ以上。|  
|`processorArchitecture`|必須。 マイクロプロセッサを指定します。 有効な値は`x86`32 ビット Windows 用と`IA64`の 64 ビット Windows です。|  
|`Language`|任意。 アセンブリの 2 部構成の言語コードを識別します。 たとえば、EN-US、英語 (米国) を意味します。 既定値は `neutral` です。 この要素は、`asmv2`名前空間。|  
|`type`|任意。 Windows によって並列との互換性が旧バージョンとテクノロジをインストールします。 唯一の許容値は`win32`します。|  
  
## <a name="hash"></a>hash  
 `hash`要素のオプションの子では、`file`要素。 `hash`要素に属性がありません。  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] デプロイ後に変更されたファイルがないことを確認するのにセキュリティ チェックとして、アプリケーションでのすべてのファイルのアルゴリズム、ハッシュを使用します。 場合、`hash`要素が含まれていない、このチェックは実行されません。 そのため、省略すると、`hash`要素はお勧めしません。  
  
## <a name="dsigtransforms"></a>dsig:Transforms  
 `dsig:Transforms`要素の必須の子では、`hash`要素。 `dsig:Transforms`要素に属性がありません。  
  
## <a name="dsigtransform"></a>dsig:Transform  
 `dsig:Transform`要素の必須の子では、`dsig:Transforms`要素。 次の表の属性を示します、`dsig:Transform`要素。  
  
|属性|説明|  
|---------------|-----------------|  
|`Algorithm`|このファイルのダイジェストを計算するために使用するアルゴリズム。 現在、唯一の値で使用される[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]は`urn:schemas-microsoft-com:HashTransforms.Identity`します。|  
  
## <a name="dsigdigestmethod"></a>dsig:DigestMethod  
 `dsig:DigestMethod`要素の必須の子では、`hash`要素。 次の表の属性を示します、`dsig:DigestMethod`要素。  
  
|属性|説明|  
|---------------|-----------------|  
|`Algorithm`|このファイルのダイジェストを計算するために使用するアルゴリズム。 現在、唯一の値で使用される[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]は`http://www.w3.org/2000/09/xmldsig#sha1`します。|  
  
## <a name="dsigdigestvalue"></a>目的  
 `dsig:DigestValue`要素の必須の子では、`hash`要素。 `dsig:DigestValue`要素に属性がありません。 テキスト値は、指定したファイルの計算されたハッシュです。  
  
## <a name="remarks"></a>Remarks  
 配置マニフェストは通常、1 つをある`assemblyIdentity`名前と、アプリケーション マニフェストのバージョンを識別する要素。  
  
## <a name="example"></a>例  
 次のコード例は、`dependency`内の要素を[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]配置マニフェスト。  
  
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
  
## <a name="example"></a>例  
 次のコード例では、GAC に既にインストールされているアセンブリの依存関係を指定します。  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="GACAssembly" version="1.0.0.0" language="neutral" processorArchitecture="msil" />  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>例  
 次のコード例では、共通言語ランタイムの特定のバージョンに依存関係を指定します。  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50215.0" />  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>例  
 次のコード例では、オペレーティング システムの依存関係を指定します。  
  
```  
<dependency>  
   <dependentOS supportUrl="http://www.microsoft.com" description="Microsoft Windows Operating System">  
      <osVersionInfo>  
         <os majorVersion="4" minorVersion="10" />  
      </osVersionInfo>  
   </dependentOS>  
</dependency>  
```  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)   
 [\<dependency> 要素](../deployment/dependency-element-clickonce-application.md)



