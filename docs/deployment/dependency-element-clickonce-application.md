---
title: '&lt;依存関係&gt;要素 (ClickOnce アプリケーション) |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
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
- manifests [ClickOnce], dependency element
- <dependency> element [ClickOnce application manifest]
ms.assetid: 09d6a1e0-60f8-4fbd-843b-8e49ee3115a3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1dbd882958c8542be1ec337386634af7dae2e70e
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078561"
---
# <a name="ltdependencygt-element-clickonce-application"></a>&lt;依存関係&gt;要素 (ClickOnce アプリケーション)
アプリケーションに必要なプラットフォームやアセンブリ依存関係を識別します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
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
  
## <a name="elements-and-attributes"></a>要素と属性  
 `dependency`要素が必要です。 複数のインスタンスがある可能性があります`dependency`アプリケーション マニフェストを同じにします。  
  
 `dependency`要素、属性を持っていないと、次の子要素が含まれています。  
  
### <a name="dependentos"></a>dependentOS  
 任意。 `osVersionInfo`要素を含んでいます。 `dependentOS`と`dependentAssembly`要素は相互に排他的: のいずれか 1 つが存在する必要があります、`dependency`両方ではなく、要素。  
  
 `dependentOS` 次の属性をサポートしています。  
  
|属性|説明|  
|---------------|-----------------|  
|`supportUrl`|任意。 依存するプラットフォームのサポート URL を指定します。 この URL は、必要なプラットフォームが見つかった場合、ユーザーに表示されます。|  
|`description`|任意。 説明されているオペレーティング システムを人間が判読できる形式は、説明、`dependentOS`要素。|  
  
### <a name="osversioninfo"></a>osVersionInfo  
 必須。 この要素は `dependentOS` 要素の子であり、`os` 要素を含んでいます。 この要素には属性はありません。  
  
### <a name="os"></a>os  
 必須。 この要素は `osVersionInfo` 要素の子です。 この要素には、次の属性があります。  
  
|属性|説明|  
|---------------|-----------------|  
|`majorVersion`|必須。 OS のメジャー バージョン番号を指定します。|  
|`minorVersion`|必須。 OS のマイナー バージョン番号を指定します。|  
|`buildNumber`|必須。 OS のビルド番号を指定します。|  
|`servicePackMajor`|必須。 OS のサービス パックのメジャー番号を指定します。|  
|`servicePackMinor`|任意。 OS のサービス パックのマイナー番号を指定します。|  
|`productType`|任意。 製品の種類の値を識別します。 有効な値は `server`、`workstation`、`domainController` です。 たとえば、Windows 2000 professional では、この属性値は`workstation`します。|  
|`suiteType`|任意。 システムまたはシステムの構成の種類で使用可能な製品スイートを識別します。 有効な値は`backoffice`、 `blade`、 `datacenter`、 `enterprise`、 `home`、 `professional`、 `smallbusiness`、 `smallbusinessRestricted`、および`terminal`します。 たとえば、Windows 2000 professional では、この属性値は`professional`します。|  
  
### <a name="dependentassembly"></a>dependentAssembly  
 任意。 `assemblyIdentity`要素を含んでいます。 `dependentOS`と`dependentAssembly`要素は相互に排他的: のいずれか 1 つが存在する必要があります、`dependency`両方ではなく、要素。  
  
 `dependentAssembly` 次の属性があります。  
  
|属性|説明|  
|---------------|-----------------|  
|`dependencyType`|必須。 依存関係の種類を指定します。 有効値は `preprequisite` または `install` です。 `install`アセンブリがの一部としてインストールされている、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション。 A`prerequisite`アセンブリは、前にグローバル アセンブリ キャッシュ (GAC) に存在する必要があります、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションをインストールできます。|  
|`allowDelayedBinding`|必須。 実行時にプログラムによって読み込むアセンブリことができるかどうかを指定します。|  
|`group`|任意。 場合、`dependencyType`属性に設定されて`install`オンデマンドでインストールするのみのアセンブリの名前付きグループを指定します。 詳細については、「[チュートリアル : デザイナーを使用し、ClickOnce 配置 API で必要に応じてアセンブリをダウンロードする](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md)」を参照してください。<br /><br /> 場合に設定`framework`と`dependencyType`属性に設定されて`prerequisite`、.NET Framework の一部として、アセンブリを指定します。 インストールする場合、このアセンブリをグローバル アセンブリ キャッシュ (GAC) がチェックされません[!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)]以降のバージョン。|  
|`codeBase`|必要なときに、`dependencyType`属性に設定されて`install`します。 依存アセンブリへのパス。 可能性があります絶対パス、または、マニフェストのコードからの相対パスのいずれかベース。 このパスは有効であるアセンブリ マニフェストの順序で、有効な URI である必要があります。|  
|`size`|必要なときに、`dependencyType`属性に設定されて`install`します。 (バイト単位) の依存アセンブリのサイズ。|  
  
### <a name="assemblyidentity"></a>assemblyIdentity  
 必須。 この要素は `dependentAssembly` 要素の子であり、以下の属性があります。  
  
|属性|説明|  
|---------------|-----------------|  
|`name`|必須。 アプリケーションの名前を識別します。|  
|`version`|必須。 次の形式で、アプリケーションのバージョン番号を指定します。 `major.minor.build.revision`|  
|`publicKeyToken`|任意。 最後の 8 バイトを表す 16 文字の 16 進文字列を指定します、`SHA-1`アプリケーションまたはアセンブリに署名するとき、公開キーのハッシュ値。 カタログに署名するために使用する公開キーは、2048 ビット以上である必要があります。|  
|`processorArchitecture`|任意。 プロセッサを指定します。 有効な値は`x86`32 ビット Windows 用と`I64`の 64 ビット Windows です。|  
|`language`|任意。 アセンブリの EN-US など、2 部構成の言語コードを識別します。|  
  
### <a name="hash"></a>hash  
 `hash`要素のオプションの子では、`assemblyIdentity`要素。 `hash`要素に属性がありません。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] デプロイ後に変更されたファイルがないことを確認するのに、セキュリティ チェックとして、アプリケーションでのすべてのファイルのアルゴリズム、ハッシュを使用します。 場合、`hash`要素が含まれていない、このチェックは実行されません。 そのため、省略すると、`hash`要素はお勧めしません。  
  
### <a name="dsigtransforms"></a>dsig:Transforms  
 `dsig:Transforms`要素の必須の子では、`hash`要素。 `dsig:Transforms`要素に属性がありません。  
  
### <a name="dsigtransform"></a>dsig:Transform  
 `dsig:Transform`要素の必須の子では、`dsig:Transforms`要素。 `dsig:Transform`要素には、次の属性。  
  
|属性|説明|  
|---------------|-----------------|  
|`Algorithm`|このファイルのダイジェストを計算するために使用するアルゴリズム。 現在、唯一の値で使用される[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]は`urn:schemas-microsoft-com:HashTransforms.Identity`します。|  
  
### <a name="dsigdigestmethod"></a>dsig:DigestMethod  
 `dsig:DigestMethod`要素の必須の子では、`hash`要素。 `dsig:DigestMethod`要素には、次の属性。  
  
|属性|説明|  
|---------------|-----------------|  
|`Algorithm`|このファイルのダイジェストを計算するために使用するアルゴリズム。 現在、唯一の値で使用される[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]は`http://www.w3.org/2000/09/xmldsig#sha1`します。|  
  
### <a name="dsigdigestvalue"></a>目的  
 `dsig:DigestValue`要素の必須の子では、`hash`要素。 `dsig:DigestValue`要素に属性がありません。 テキスト値は、指定したファイルの計算されたハッシュです。  
  
## <a name="remarks"></a>Remarks  
 アプリケーションによって使用されるすべてのアセンブリの対応する必要があります`dependency`要素。 依存アセンブリでは、プラットフォーム アセンブリとグローバル アセンブリ キャッシュにプレインストールする必要がありますアセンブリは含まれません。  
  
## <a name="example"></a>例  
 次のコード例を示しています`dependency`内の要素を[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション マニフェスト。 このコード例が示されている例の一部、 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)トピック。  
  
```xml  
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
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)   
 [\<依存関係 > 要素](../deployment/dependency-element-clickonce-deployment.md)