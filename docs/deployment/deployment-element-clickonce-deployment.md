---
title: "&lt;deployment&gt; 要素 (ClickOnce 配置) | Microsoft Docs"
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
  - "urn:schemas-microsoft-com:asm.v2#subscription"
  - "urn:schemas-microsoft-com:asm.v2#beforeApplicationStartup"
  - "urn:schemas-microsoft-com:asm.v2#deploymentProvider"
  - "urn:schemas-microsoft-com:asm.v2#update"
  - "urn:schemas-microsoft-com:asm.v2#deployment"
  - "urn:schemas-microsoft-com:asm.v2#expiration"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<deployment> 要素 [ClickOnce 配置マニフェスト]"
ms.assetid: 4fafa9c2-97a0-4cea-b8fd-9746dca33af4
caps.latest.revision: 30
caps.handback.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;deployment&gt; 要素 (ClickOnce 配置)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

更新プログラムの配置とシステムへの公開に使用される属性を指定します。  
  
## 構文  
  
```  
  
      <deployment   
   install  
   minimumRequiredVersion  
   mapFileExtensions  
   disallowUrlActivation  
   trustUrlParameters  
>   
   <subscription>   
         <update>   
            <beforeApplicationStartup/>   
            <expiration  
               maximumAge  
               unit  
            />  
         </update>    
   </subscription>   
   <deploymentProvider   
      codebase   
   />   
</deployment>  
```  
  
## 要素と属性  
 `deployment` 要素は必須で、`urn:schemas-microsoft-com:asm.v1` 名前空間にあります。  この要素には、次の属性があります。  
  
|属性|Description|  
|--------|-----------------|  
|`install`|必ず指定します。  このアプリケーションを、Windows の **\[スタート\]** メニューおよびコントロール パネルの **\[プログラムの追加と削除\]** に登録するかどうかを指定します。  有効な値は、`true` および `false` です。  `false` を設定した場合は、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] によって常にネットワークからアプリケーションの最新バージョンが実行され、`subscription` 要素は認識されません。|  
|`minimumRequiredVersion`|省略可能です。  クライアントで実行できる、このアプリケーションの最低限のバージョンを指定します。  アプリケーションのバージョン番号が、配置マニフェストで指定されているよりも前のバージョン番号の場合、アプリケーションは実行されません。  バージョン番号は `N.N.N.N` という形式で指定する必要があります。`N` は符号なし整数です。  `install` 属性が `false` である場合は、`minimumRequiredVersion` を指定できません。|  
|`mapFileExtensions`|省略可能です。  既定値は `false` です。  `true` にした場合、配置のすべてのファイルの拡張子が .deploy になります。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] では、Web サーバーからのダウンロードが完了すると、これらのファイルからこの拡張子を削除します。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] を使用してアプリケーションを公開する場合は、すべてのファイルに自動的にこの拡張子が追加されます。  このパラメーターは、.exe などの安全が保証されない拡張子が付いているファイルの転送をブロックする Web サーバーから [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 配置のすべてのファイルをダウンロードできるようにします。|  
|`disallowUrlActivation`|省略可能です。  既定値は `false` です。  `true` の場合、URL をクリックするか、または Internet Explorer に URL を入力することによってインストールされているアプリケーションを起動できないようにします。  `install` 属性がない場合、この属性は無視されます。|  
|`trustURLParameters`|省略可能です。  既定値は `false` です。  `true` の場合、コマンド ライン アプリケーションにコマンド ライン引数を渡すことができるように、アプリケーションに渡されるクエリ文字列パラメーターを URL に含めることができるようになります。  詳細については、「[方法 : オンライン ClickOnce アプリケーションでクエリ文字列を取得する](../Topic/How%20to:%20Retrieve%20Query%20String%20Information%20in%20an%20Online%20ClickOnce%20Application.md)」を参照してください。<br /><br /> `disallowUrlActivation` 属性が `true` の場合は、`trustUrlParameters` をマニフェストから排除するか、または明示的に `false` に設定する必要があります。|  
  
 `deployment` 要素には、次の子要素もあります。  
  
## subscription  
 省略可能です。  `update` 要素を含みます。  `subscription` 要素に属性はありません。  `subscription` 要素が存在しない場合、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションでは、更新プログラムの確認が行われません。  `deployment` 要素の `install` 属性が `false` に設定してある場合、`subscription` 要素は無視されます。この場合には、ネットワークから [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションが起動されて、常に最新バージョンが使用されるためです。  
  
## update  
 必ず指定します。  この要素は `subscription` 要素の子であり、`beforeApplicationStartup` 要素または `expiration` 要素が含まれています。  同じ配置マニフェストに、`beforeApplicationStartup` と `expiration` の両方は指定できません。  
  
 `update` 要素に属性はありません。  
  
## beforeApplicationStartup  
 省略可能です。  この要素は `update` 要素の子であり、属性はありません。  `beforeApplicationStartup` 要素が存在し、クライアントがオンラインの場合、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] で更新プログラムを確認する際にアプリケーションの実行がブロックされます。  この要素が存在しない場合、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] は、`expiration` 要素に指定された値に基づいて最初に更新プログラムの確認を行います。  同じ配置マニフェストに、`beforeApplicationStartup` と `expiration` の両方は指定できません。  
  
## expiration  
 省略可能です。  この要素は `update` 要素の子であり、子の要素はありません。  同じ配置マニフェストに、`beforeApplicationStartup` と `expiration` の両方は指定できません。  更新プログラムのチェックが発生し、更新バージョンが検出された場合、既存のバージョンの実行中に新しいバージョンがキャッシュされます。  新しいバージョンは、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションの次の起動時にインストールされます。  
  
 `expiration` 要素は、次の属性をサポートします。  
  
|属性|Description|  
|--------|-----------------|  
|`maximumAge`|必ず指定します。  アプリケーションで最後に更新を実行してから次の更新プログラムの確認を行うまでの期間を指定します。  時間の単位は、`unit` 属性で指定します。|  
|`unit`|必ず指定します。  `maximumAge` 属性の時間の単位を指定します。  有効な単位は、`hours`、`days`、および `weeks` です。|  
  
## deploymentProvider  
 .NET Framework 2.0 の場合、配置マニフェストに `subscription` セクションがある場合、この要素は必須です。  .NET Framework 3.5 以降の場合、この要素は省略できます。既定で、サーバーおよびファイルのパスが設定され、ここで配置マニフェストが検出されます。  
  
 この要素は `deployment` 要素の子であり、以下の属性があります。  
  
|属性|Description|  
|--------|-----------------|  
|`codebase`|必ず指定します。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションを更新するための配置マニフェストの場所を、URI \(Uniform Resource Identifier\) として指定します。  この要素は、CD ベースのインストールで、更新プログラムの場所を変更するために使用することもできます。  有効な URI を指定する必要があります。|  
  
## 解説  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションは、更新プログラムの確認を起動時に行うか、起動後に行うか、または更新の確認を実行しないように設定できます。  起動時に更新プログラムを確認するには、`update` 要素に `beforeApplicationStartup` 要素を設定します。  起動後に更新プログラムを確認するには、`update` 要素に `expiration` 要素を設定し、更新間隔を指定します。  
  
 更新プログラムを確認しないようにするには、`subscription` 要素を削除します。  配置マニフェストで更新プログラムを確認しないように指定した場合でも、<xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A> メソッドを使用して手動で更新プログラムを確認できます。  
  
 deploymentProvider を更新プログラムと関連付ける方法の詳細については、「[ClickOnce の更新方法の選択](../deployment/choosing-a-clickonce-update-strategy.md)」を参照してください。  
  
## 例  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 配置マニフェスト内の `deployment` 要素を次のコード例に示します。  この例では、`deploymentProvider` 要素を使用して、目的の更新プログラムの場所を指定しています。  
  
```  
<deployment install="true" minimumRequiredVersion="2.0.0.0" mapFileExtension="true" trustUrlParameters="true">  
    <subscription>  
      <update>  
        <expiration maximumAge="6" unit="hours" />  
      </update>  
    </subscription>  
    <deploymentProvider codebase="http://www.adatum.com/MyApplication.application" />  
  </deployment>  
```  
  
## 参照  
 [ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)