---
title: '&lt;依存関係&gt;要素 (ClickOnce 配置) |Microsoft ドキュメント'
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
- <dependency> element [ClickOnce deployment manifest]
ms.assetid: 9b4d2082-0347-4922-ac70-85f11b913039
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 72e217413a428c8c22712ac3a90836b1ea4fbc35
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="ltdependencygt-element-clickonce-deployment"></a>&lt;依存関係&gt;要素 (ClickOnce 配置)
をインストールするアプリケーションのバージョン、およびアプリケーション マニフェストの場所を識別します。  
  
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
  
 `dependency`要素は通常内に含まれるアセンブリに、メイン アプリケーションの依存関係を表す、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションです。 Main.exe アプリケーションは、DotNetAssembly.dll という名前のアセンブリを消費する場合、そのアセンブリは依存関係セクションに表示する必要があります。 依存関係、ただし、表すことも他の種類など、共通言語ランタイムの特定のバージョンへの依存関係の依存関係のグローバル アセンブリ キャッシュ (GAC) 内のアセンブリまたは COM オブジェクトです。 配置テクノロジになっているため[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]防ぐことはできませんの依存関係のこれらの型の初期化のダウンロードとインストールは、アプリケーションの実行、指定した依存関係の 1 つ以上が存在しない場合。  
  
## <a name="dependentassembly"></a>dependentAssembly  
 必須。 この要素が含まれています、`assemblyIdentity`要素。 次の表は、属性、`dependentAssembly`をサポートしています。  
  
|属性|説明|  
|---------------|-----------------|  
|`preRequisite`|任意。 このアセンブリが GAC に既に存在する必要があるを指定します。 有効値は `true` または `false` です。 場合`true`、指定したアセンブリが GAC に存在しないと、アプリケーションの実行に失敗しました。|  
|`visible`|任意。 依存関係を含む、最上位のアプリケーション id を識別します。 によって内部的に使用される[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション記憶域とアクティブ化を管理します。|  
|`dependencyType`|必須。 この依存関係と、アプリケーション間のリレーションシップ。 次の値を指定できます。<br /><br /> -   `install`. コンポーネントでは、現在のアプリケーションから別のインストールを表します。<br />-   `preRequisite`. コンポーネントは、現在のアプリケーションが必要です。|  
|`codebase`|任意。 アプリケーション マニフェストの完全パスです。|  
|`size`|任意。 アプリケーション マニフェストがバイト単位のサイズ。|  
  
## <a name="assemblyidentity"></a>assemblyIdentity  
 必須。 この要素は `dependentAssembly` 要素の子です。 コンテンツ`assemblyIdentity`で説明されていることと同じである必要があります、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション マニフェスト。 次の表の属性を示しています、`assemblyIdentity`要素。  
  
|属性|説明|  
|---------------|-----------------|  
|`Name`|必須。 アプリケーションの名前を識別します。|  
|`Version`|必須。 次の形式で、アプリケーションのバージョン番号を指定します。 `major.minor.build.revision`|  
|`publicKeyToken`|必須。 アプリケーションまたはアセンブリが署名に使用されたパブリック キーの sha-1 ハッシュの最後の 8 バイトを表す 16 文字の 16 進文字列を指定します。 署名に使用される公開キーは 2048 ビットである必要がありますか値を超えています。|  
|`processorArchitecture`|必須。 マイクロプロセッサを指定します。 有効な値は`x86`32 ビット Windows 用と`IA64`64 ビット Windows 用です。|  
|`Language`|任意。 アセンブリの 2 部構成の言語コードを識別します。 たとえば、EN-US、英語 (米国) を意味します。 既定値は、`neutral` です。 この要素は、`asmv2`名前空間。|  
|`type`|任意。 Windows サイド バイ サイドとの互換性が旧バージョンとテクノロジをインストールします。 許可されている値だけ`win32`です。|  
  
## <a name="hash"></a>hash  
 `hash`要素の省略可能な子では、`file`要素。 `hash`要素に属性がありません。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 展開後に変更されたファイルがないことを確認するのに、セキュリティ チェックとして、アプリケーション内のすべてのファイルのアルゴリズムのハッシュを使用します。 場合、`hash`要素が含まれていない、このチェックは実行されません。 そのため、省略すると、`hash`要素はお勧めしません。  
  
## <a name="dsigtransforms"></a>dsig:Transforms  
 `dsig:Transforms`要素の必須の子では、`hash`要素。 `dsig:Transforms`要素に属性がありません。  
  
## <a name="dsigtransform"></a>dsig:Transform  
 `dsig:Transform`要素の必須の子では、`dsig:Transforms`要素。 次の表の属性を示しています、`dsig:Transform`要素。  
  
|属性|説明|  
|---------------|-----------------|  
|`Algorithm`|このファイルのダイジェストを計算するために使用するアルゴリズムです。 現在、唯一の値で使用される[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]は`urn:schemas-microsoft-com:HashTransforms.Identity`します。|  
  
## <a name="dsigdigestmethod"></a>dsig:DigestMethod  
 `dsig:DigestMethod`要素の必須の子では、`hash`要素。 次の表の属性を示しています、`dsig:DigestMethod`要素。  
  
|属性|説明|  
|---------------|-----------------|  
|`Algorithm`|このファイルのダイジェストを計算するために使用するアルゴリズムです。 現在、唯一の値で使用される[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]は`http://www.w3.org/2000/09/xmldsig#sha1`します。|  
  
## <a name="dsigdigestvalue"></a>目的  
 `dsig:DigestValue`要素の必須の子では、`hash`要素。 `dsig:DigestValue`要素に属性がありません。 テキスト値は、指定したファイルの計算されたハッシュです。  
  
## <a name="remarks"></a>コメント  
 配置マニフェストは通常、1 つをある`assemblyIdentity`名前とアプリケーション マニフェストのバージョンを識別する要素。  
  
## <a name="example"></a>例  
 次のコード例は、`dependency`内の要素、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]配置マニフェスト。  
  
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