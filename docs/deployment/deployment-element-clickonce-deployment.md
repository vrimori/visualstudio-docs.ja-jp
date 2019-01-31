---
title: '&lt;展開&gt;要素 (ClickOnce 配置) |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
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
helpviewer_keywords:
- <deployment> element [ClickOnce deployment manifest]
ms.assetid: 4fafa9c2-97a0-4cea-b8fd-9746dca33af4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 55035a214d98abd262f85c29c55bd633c0b35505
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55023721"
---
# <a name="ltdeploymentgt-element-clickonce-deployment"></a>&lt;展開&gt;要素 (ClickOnce 配置)
更新プログラムの配置とシステムへの公開に使用される属性を指定します。  

## <a name="syntax"></a>構文  

```xml  

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


| 属性 | 説明 |
|--------------------------| - |
| `install` | 必須です。 このアプリケーションが、Windows の存在を定義するかどうかを指定します。**開始**メニューや コントロール パネル**プログラム追加と削除**アプリケーション。 有効値は `true` または `false` です。 場合`false`、 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 、ネットワークからこのアプリケーションの最新バージョンは常に実行してが認識しない、`subscription`要素。 |
| `minimumRequiredVersion` | 任意。 このクライアントで実行できるアプリケーションの最小バージョンを指定します。 アプリケーションのバージョン番号が、配置マニフェストで指定されたバージョン番号よりも小さい場合は、アプリケーションは実行されません。 形式でバージョン番号を指定する必要があります`N.N.N.N`ここで、`N`は符号なし整数です。 場合、`install`属性が`false`、`minimumRequiredVersion`設定する必要があります。 |
| `mapFileExtensions` | 任意。 既定値は `false` です。 場合`true`展開内のすべてのファイルが .deploy 拡張子をいる必要があります。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] これらのファイルを Web サーバーからそれらをダウンロードするとすぐにこの拡張機能がストリップされます。 使用してアプリケーションを発行する場合[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、すべてのファイルに自動的にこの拡張機能を追加します。 このパラメーターにより、すべてのファイルを[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]「アンセーフ」拡張子 .exe などで終わるファイルの転送をブロックする Web サーバーからダウンロードして展開します。 |
| `disallowUrlActivation` | 任意。 既定値は `false` です。 場合`true`、により、インストールされているアプリケーションから開始して、URL をクリックするか、Internet Explorer に URL を入力します。 場合、`install`属性が存在しない場合、この属性は無視されます。 |
| `trustURLParameters` | 任意。 既定値は `false` です。 場合`true`、により、アプリケーションに渡されるクエリ文字列パラメーターを格納する URL、コマンド ライン アプリケーションに渡された量などのコマンドライン引数。 詳細については、「[方法 :オンライン ClickOnce アプリケーションでクエリ文字列の情報を取得する](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)」を参照してください。<br /><br /> 場合、`disallowUrlActivation`属性が`true`、`trustUrlParameters`か必要がありますが、マニフェストから除外明示的に設定`false`します。 |

 `deployment`要素には、次の子要素も含まれています。  

## <a name="subscription"></a>subscription  
 任意。 含まれています、`update`要素。 `subscription` 要素に属性はありません。 場合、`subscription`要素が存在しない、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションが更新プログラム スキャンことはありません。 場合、`install`の属性、`deployment`要素は`false`、`subscription`要素が無視されます、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]常に、ネットワークから起動されるアプリケーションは、最新バージョンを使用します。  

## <a name="update"></a>更新  
 必須です。 この要素の子である、`subscription`要素を含む、`beforeApplicationStartup`または`expiration`要素。 `beforeApplicationStartup` `expiration`両方を同じ配置マニフェストで指定することはできません。  

 `update` 要素に属性はありません。  

## <a name="beforeapplicationstartup"></a>beforeApplicationStartup  
 任意。 この要素の子である、`update`要素属性を持っていません。 ときに、`beforeApplicationStartup`要素が存在すると、アプリケーションがなるときにブロックされている[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]クライアントがオンラインの場合、更新プログラムを確認します。 この要素が存在しない場合[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]が最初に指定された値に基づいて更新プログラム スキャン、`expiration`要素。 `beforeApplicationStartup` `expiration`両方を同じ配置マニフェストで指定することはできません。  

## <a name="expiration"></a>expiration  
 任意。 この要素の子である、`update`要素、子を持っていないとします。 `beforeApplicationStartup` `expiration`両方を同じ配置マニフェストで指定することはできません。 更新チェックが発生し、更新されたバージョンが検出された、新しいバージョンを既存のバージョンの実行中にキャッシュします。 次回の起動時に、新しいバージョンをインストールし、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション。  

 `expiration`要素は、次の属性をサポートしています。  

|属性|説明|  
|---------------|-----------------|  
|`maximumAge`|必須です。 古さ現在の更新する必要がありますになるまで、アプリケーション更新チェックが実行を識別します。 時間の単位がによって決定されます、`unit`属性。|  
|`unit`|必須です。 時間の単位を識別する`maximumAge`します。 有効な単位は`hours`、 `days`、および`weeks`します。|  

## <a name="deploymentprovider"></a>deploymentProvider  
 .NET Framework 2.0 では、この要素が必要です、配置マニフェストが含まれている場合、`subscription`セクション。 .NET Framework 3.5 以降、この要素はオプションですとサーバーと配置マニフェストが検出されたファイル パスには既定で。  

 この要素は `deployment` 要素の子であり、以下の属性があります。  


| 属性 | 説明 |
|------------| - |
| `codebase` | 必須です。 場所を識別、としてする Uniform Resource Identifier (URI)、更新に使用される配置マニフェスト、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション。 この要素も CD ベースのインストールの更新プログラムの場所を転送をできます。 有効な URI である必要があります。 |

## <a name="remarks"></a>コメント  
 構成することができます、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]スタートアップ時に、更新プログラムをスキャンするアプリケーションの開始の後、更新プログラムをスキャンまたは更新プログラムを確認しません。 起動時に更新プログラムをスキャンすることを確認、`beforeApplicationStartup`下の要素が存在する、`update`要素。 起動後に更新プログラムのスキャン、することを確認、`expiration`下の要素が存在する、`update`要素、および更新間隔が提供されます。  

 更新プログラムのチェックを無効にするには削除、`subscription`要素。 しない更新プログラムをスキャンする配置マニフェストで指定する場合は手動で更新を確認するを使用して、<xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A>メソッド。  

 DeploymentProvider 更新プログラムに関連付ける方法の詳細については、次を参照してください。 [ClickOnce の更新方法の選択](../deployment/choosing-a-clickonce-update-strategy.md)します。  

## <a name="examples"></a>使用例  
 次のコード例を示しています、`deployment`内の要素を[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]配置マニフェスト。 この例では、`deploymentProvider`を優先される更新プログラムの場所を示す要素。  

```xml  
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
 [ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)
