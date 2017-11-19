---
title: "&lt;entryPoint&gt;要素 (ClickOnce アプリケーション) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
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
caps.latest.revision: "33"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: eb280684f0c06391bc6c0596093c01f260f685d3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="ltentrypointgt-element-clickonce-application"></a>&lt;entryPoint&gt;要素 (ClickOnce アプリケーション)
識別する必要のあるアセンブリ実行すると実行この[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]クライアント コンピューターでアプリケーションを実行します。  
  
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
 `entryPoint` 要素は必須です。この要素は `urn:schemas-microsoft-com:asm.v2` 名前空間に属します。 のみがありますいずれかの`entryPoint`アプリケーション マニフェストで定義された要素。  
  
 `entryPoint`要素には、次の属性です。  
  
|属性|説明|  
|---------------|-----------------|  
|`name`|省略可能です。 この値は、.NET Framework では使用されません。|  
  
 `entryPoint`次の要素があります。  
  
## <a name="assemblyidentity"></a>assemblyIdentity  
 必須です。 役割`assemblyIdentity`でその属性が定義されていると[ \<assemblyIdentity > 要素](../deployment/assemblyidentity-element-clickonce-application.md)です。  
  
 `processorArchitecture`この要素の属性と`processorArchitecture`属性で定義されている、`assemblyIdentity`別の場所で、アプリケーション マニフェストと一致しなければなりません。  
  
## <a name="commandline"></a>コマンドライン  
 必ず指定します。 子である必要があります、`entryPoint`要素。 子要素が存在しないと、次の属性があります。  
  
|属性|説明|  
|---------------|-----------------|  
|`file`|必須です。 ローカル アセンブリへの参照、スタートアップの[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションです。 この値は、スラッシュ (/) または円記号を含めることはできません (\\) パスの区切り記号。|  
|`parameters`|必須です。 エントリ ポイントで実行するアクションを説明します。 唯一の有効な値は`run`以外の場合は、空の文字列を指定すると、`run`と見なされます。|  
  
## <a name="customhostrequired"></a>customHostRequired  
 省略可能です。 含まれる場合は、この展開にはでのカスタム ホスト内で展開されるコンポーネントが含まれているを指定し、スタンドアロンのアプリケーションではありません。  
  
 この要素が存在する場合、`assemblyIdentity`と`commandLine`要素もすることはできませんに存在します。 その場合は、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]インストール中に検証エラーが発生します。  
  
 この要素にはない属性と子はありません。  
  
## <a name="customux"></a>customUX  
 省略可能です。 アプリケーションがインストールされているとカスタム インストーラーによって管理されるとはされませんスタート メニュー エントリ、ショートカット、または追加作成するか指定しますプログラム エントリを削除します。  
  
```  
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />  
```  
  
 アプリケーションを customUX 要素を含む必要がありますを提供するカスタム インストーラーを使用して、<xref:System.Deployment.Application.InPlaceHostingManager>を実行するクラスは、操作をインストールします。 この要素を持つアプリケーションは、そのマニフェストまたは setup.exe 前提条件となるブートス トラップをダブルクリックしてインストールできません。 カスタム インストーラーには、スタート メニュー エントリ、ショートカット、およびプログラム追加と削除のエントリを作成できます。 によって提供されたサブスクリプション識別子を格納する必要があります、カスタム インストーラーが追加または削除するプログラムのエントリを作成できない場合、<xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A>プロパティと有効にするアプリケーションをアンインストールした後で呼び出すことによって、ユーザー、<xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A>メソッドです。 詳細については、次を参照してください。[チュートリアル: ClickOnce アプリケーションのカスタム インストーラーを作成する](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md)です。  
  
## <a name="remarks"></a>コメント  
 この要素のアセンブリとエントリ ポイントを識別する、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションです。  
  
 使用することはできません`commandLine`パラメーターを渡すを実行時にアプリケーションにします。 クエリ文字列パラメーターにアクセスすることができます、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]からアプリケーションの展開<xref:System.AppDomain>です。 詳細については、次を参照してください。[する方法: オンライン ClickOnce アプリケーションを使用したクエリ文字列情報を取得](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)です。  
  
## <a name="example"></a>例  
 次のコード例を示しています、`entryPoint`アプリケーション マニフェストの要素、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションです。 このコード例に示されている例の一部である、 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)トピックです。  
  
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