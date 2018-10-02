---
title: '&lt;entryPoint&gt;要素 (ClickOnce アプリケーション) |Microsoft Docs'
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
- urn:schemas-microsoft-com:asm.v2#commandLine
- urn:schemas-microsoft-com:asm.v2#entryPoint
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <entryPoint> element [ClickOnce application manifest]
- manifests [ClickOnce], entryPoint element
ms.assetid: 10ad3083-10c1-4189-a870-9bba2eab244f
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 05e8e08718d9a0a87a1a3903e512c690ab0ebff8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547954"
---
# <a name="ltentrypointgt-element-clickonce-application"></a>&lt;entryPoint&gt;要素 (ClickOnce アプリケーション)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ &lt;entryPoint&gt;要素 (ClickOnce アプリケーション)](https://docs.microsoft.com/visualstudio/deployment/entrypoint-element-clickonce-application)します。  
  
必要のあるアセンブリを識別するときに実行この[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]クライアント コンピューターでアプリケーションを実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
      <entryPoint  
   name  
>  
   <assemblyIdentity  
      name  
      version  
      processorArchitecture  
      language  
   />  
   <commandLine  
      file  
      parameters  
   />  
   <customHostRequired />  
   <customUX />  
</entryPoint>  
```  
  
## <a name="elements-and-attributes"></a>要素と属性  
 `entryPoint` 要素は必須です。この要素は `urn:schemas-microsoft-com:asm.v2` 名前空間に属します。 ある可能性がありますのみ 1 つ`entryPoint`アプリケーション マニフェストで定義された要素。  
  
 `entryPoint`要素には、次の属性。  
  
|属性|説明|  
|---------------|-----------------|  
|`name`|任意。 この値は、.NET Framework では使用されません。|  
  
 `entryPoint` 次の要素があります。  
  
## <a name="assemblyidentity"></a>assemblyIdentity  
 必須。 ロール`assemblyIdentity`でその属性が定義されていると[ \<assemblyIdentity > 要素](../deployment/assemblyidentity-element-clickonce-application.md)します。  
  
 `processorArchitecture`この要素の属性と`processorArchitecture`属性で定義されている、`assemblyIdentity`別の場所、アプリケーション マニフェストと一致しなければなりません。  
  
## <a name="commandline"></a>コマンドライン  
 必須。 子である必要があります、`entryPoint`要素。 子要素が存在しないと、次の属性があります。  
  
|属性|説明|  
|---------------|-----------------|  
|`file`|必須。 スタートアップ アセンブリへの参照をローカル、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]アプリケーション。 この値は、スラッシュ (/) または円記号を含めることはできません (\\) パスの区切り記号。|  
|`parameters`|必須。 エントリ ポイントで実行するアクションをについて説明します。 唯一の有効な値は`run`場合は、空の文字列は、指定した`run`と見なされます。|  
  
## <a name="customhostrequired"></a>customHostRequired  
 任意。 に含まれている場合は、この配置にカスタム ホストの内部で展開されるコンポーネントが含まれているを指定し、スタンドアロン アプリケーションではありません。  
  
 この要素が存在する場合、`assemblyIdentity`と`commandLine`要素も存在してはなりません。 その場合は、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]のインストール時に検証エラーが発生します。  
  
 この要素にはない属性と子がありません。  
  
## <a name="customux"></a>customUX  
 任意。 アプリケーションがインストールされていると、カスタム インストーラーによって管理されると作成 [スタート] メニューのエントリ、ショートカット、または追加やしませんプログラムのエントリを削除するを指定します。  
  
```  
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />  
```  
  
 CustomUX 要素が含まれているアプリケーションは、カスタム インストーラーを提供する必要がありますを使用して、<xref:System.Deployment.Application.InPlaceHostingManager>を実行するクラスは、操作をインストールします。 この要素を持つアプリケーションは、そのマニフェストまたは setup.exe 前提条件となるブートス トラップをダブルクリックしてインストールできません。 カスタム インストーラーには、スタート メニュー エントリ、ショートカット、およびプログラム追加と削除のエントリを作成できます。 によって提供されたサブスクリプション識別子を格納する必要があります、カスタム インストーラーが追加または削除するプログラムのエントリを作成できない場合、<xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A>プロパティと呼び出すことによって後でアプリケーションをアンインストールするユーザーの有効化、<xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A>メソッド。 詳細については、次を参照してください。[チュートリアル: ClickOnce アプリケーションのカスタム インストーラーを作成する](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md)します。  
  
## <a name="remarks"></a>Remarks  
 この要素のアセンブリとエントリ ポイントを識別する、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]アプリケーション。  
  
 使用することはできません`commandLine`パラメーターを実行時に、アプリケーションに渡します。 クエリ文字列パラメーターにアクセスすることができます、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]からアプリケーションのデプロイを<xref:System.AppDomain>します。 詳細については、次を参照してください。[方法: オンライン ClickOnce アプリケーションでのクエリ文字列情報の取得](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)します。  
  
## <a name="example"></a>例  
 次のコード例を示しています、`entryPoint`に対するアプリケーション マニフェスト内の要素を[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]アプリケーション。 このコード例が示されている例の一部、 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)トピック。  
  
```  
<!-- Identify the main code entrypoint. -->  
<!-- This code runs the main method in an executable assembly. -->  
  <entryPoint>  
    <assemblyIdentity   
      name="MyApplication"   
      version="1.0.0.0"  
      language="neutral"  
      processorArchitecture="x86" />  
    <commandLine file="MyApplication.exe" parameters="" />  
  </entryPoint>  
```  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)



