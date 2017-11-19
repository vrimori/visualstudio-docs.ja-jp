---
title: "&lt;展開&gt;要素 (ClickOnce 配置) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#subscription
- urn:schemas-microsoft-com:asm.v2#beforeApplicationStartup
- urn:schemas-microsoft-com:asm.v2#deploymentProvider
- urn:schemas-microsoft-com:asm.v2#update
- urn:schemas-microsoft-com:asm.v2#deployment
- urn:schemas-microsoft-com:asm.v2#expiration
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords: <deployment> element [ClickOnce deployment manifest]
ms.assetid: 4fafa9c2-97a0-4cea-b8fd-9746dca33af4
caps.latest.revision: "30"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: ddcdc96095775f5957fbc9db872b51396798ba52
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="ltdeploymentgt-element-clickonce-deployment"></a>&lt;展開&gt;要素 (ClickOnce 配置)
更新プログラムの配置とシステムへの公開に使用される属性を指定します。  
  
## <a name="syntax"></a>構文  
  
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
  
## <a name="elements-and-attributes"></a>要素と属性  
 `deployment` 要素は必須です。この要素は `urn:schemas-microsoft-com:asm.v1` 名前空間に属します。 要素には、次の属性があります。  
  
|属性|説明|  
|---------------|-----------------|  
|`install`|必須です。 このアプリケーションが windows のな存在感を定義するかどうかを示す**開始**メニューや コントロール パネル**プログラム追加と削除**アプリケーションです。 有効値は `true` または `false` です。 場合`false`、 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 、ネットワークからこのアプリケーションの最新バージョンを常に実行され、認識できず、`subscription`要素。|  
|`minimumRequiredVersion`|省略可能です。 このクライアントで実行できるアプリケーションの最小バージョンを指定します。 アプリケーションのバージョン番号が、配置マニフェストで指定されたバージョン番号よりも小さい場合は、アプリケーションは実行されません。 形式でバージョン番号を指定する必要があります`N.N.N.N`ここで、`N`符号なし整数です。 場合、`install`属性は`false`、`minimumRequiredVersion`に設定しないでください。|  
|`mapFileExtensions`|省略可能です。 既定値は `false` です。 場合`true`展開内のすべてのファイルが .deploy 拡張子を持つ必要があります。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Web サーバーからダウンロードするとすぐに、これらのファイルをこの拡張機能が除去されます。 使用してアプリケーションを発行する場合[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、すべてのファイルに自動的にこの拡張機能を追加します。 このパラメーターにより、すべてのファイルを[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].exe などの拡張機能を"unsafe"で終わるファイルの転送をブロックする Web サーバーからダウンロードすることを展開します。|  
|`disallowUrlActivation`|省略可能です。 既定値は `false` です。 場合`true`URL をクリックするか、Internet Explorer に URL を入力して開始されてからインストールされたアプリケーションを防止します。 場合、`install`属性が存在しない場合、この属性は無視されます。|  
|`trustURLParameters`|省略可能です。 既定値は `false` です。 場合`true`、により、アプリケーションに渡されるクエリ文字列パラメーターを格納する URL、コマンド ライン アプリケーションに渡される程度 like コマンドライン引数。 詳細については、次を参照してください。[する方法: オンライン ClickOnce アプリケーションを使用したクエリ文字列情報を取得](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)です。<br /><br /> 場合、`disallowUrlActivation`属性は`true`、`trustUrlParameters`必要がある、マニフェストから除外されるかを明示的に設定`false`です。|  
  
 `deployment`要素には、次の子要素も含まれています。  
  
## <a name="subscription"></a>サブスクリプション  
 省略可能です。 含まれています、`update`要素。 `subscription`要素に属性がありません。 場合、`subscription`要素が存在しない、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションは更新プログラムのスキャンことはありません。 場合、`install`の属性、`deployment`要素は`false`、`subscription`要素が無視されるため、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]常に、ネットワークから起動されるアプリケーションは、最新バージョンを使用します。  
  
## <a name="update"></a>更新  
 必ず指定します。 この要素の子である、`subscription`要素いずれかが含まれています、`beforeApplicationStartup`または`expiration`要素。 `beforeApplicationStartup`および`expiration`両方を同じ配置マニフェストに指定することはできません。  
  
 `update`要素に属性がありません。  
  
## <a name="beforeapplicationstartup"></a>beforeApplicationStartup  
 省略可能です。 この要素の子である、`update`要素と属性を持っていません。 ときに、`beforeApplicationStartup`要素が存在する、アプリケーションはブロックされている場合に[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]場合、クライアントはオンラインの更新をチェックします。 この要素が存在しない場合[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]は、最初の指定された値に基づいて更新プログラムのスキャン、`expiration`要素。 `beforeApplicationStartup`および`expiration`両方を同じ配置マニフェストに指定することはできません。  
  
## <a name="expiration"></a>有効期限  
 省略可能です。 この要素の子である、`update`要素、子を持っていないとします。 `beforeApplicationStartup`および`expiration`両方を同じ配置マニフェストに指定することはできません。 更新チェックが発生し、更新されたバージョンが検出された、新しいバージョンが、既存のバージョンの実行中にキャッシュします。 次回起動時に、新しいバージョンをインストールし、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションです。  
  
 `expiration`要素は、次の属性をサポートしています。  
  
|属性|説明|  
|---------------|-----------------|  
|`maximumAge`|必須です。 どれだけ古い現在更新する必要がありますになるまでアプリケーション更新チェックが実行を識別します。 時間の単位がによって決定されます、`unit`属性。|  
|`unit`|必須です。 時間の単位を識別`maximumAge`です。 有効な単位は`hours`、 `days`、および`weeks`です。|  
  
## <a name="deploymentprovider"></a>deploymentProvider  
 .NET Framework 2.0 のこの要素は必須、配置マニフェストが含まれている場合、`subscription`セクションです。 .NET Framework 3.5 以降、この要素はオプションですは既定で、サーバーと、配置マニフェストが検出されたファイルのパスにします。  
  
 この要素は `deployment` 要素の子であり、以下の属性があります。  
  
|属性|説明|  
|---------------|-----------------|  
|`codebase`|必須です。 位置を識別、として、Uniform Resource Identifier ()、更新に使用される配置マニフェスト、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションです。 この要素は、CD ベースのインストールの更新プログラムの場所を転送する場合もできます。 有効な URI である必要があります。|  
  
## <a name="remarks"></a>コメント  
 構成することができます、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]スタートアップ時に、更新プログラムをスキャンするアプリケーションの開始の後、更新プログラムをスキャンまたは更新プログラムを確認しません。 起動時に更新プログラムをスキャンすることを確認、`beforeApplicationStartup`下にある要素が存在する、`update`要素。 起動後に更新プログラムのスキャン、いることを確認、`expiration`下にある要素が存在する、`update`要素、および更新間隔が提供されます。  
  
 更新プログラムのチェックを無効にするには削除、`subscription`要素。 更新プログラムをスキャンしないに配置マニフェストで指定すると、手動で確認できますの更新プログラムを使用して、<xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A>メソッドです。  
  
 DeploymentProvider が更新プログラムに関連付ける方法の詳細については、次を参照してください。 [ClickOnce の更新方法の選択](../deployment/choosing-a-clickonce-update-strategy.md)です。  
  
## <a name="examples"></a>例  
 次のコード例を示しています、`deployment`内の要素、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]配置マニフェスト。 この例では、`deploymentProvider`を推奨される更新プログラムの場所を示す要素。  
  
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
  
## <a name="see-also"></a>関連項目  
 [ClickOnce 配置マニフェス](../deployment/clickonce-deployment-manifest.md)