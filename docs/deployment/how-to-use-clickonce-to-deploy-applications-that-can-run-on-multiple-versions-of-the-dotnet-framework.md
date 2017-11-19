---
title: "方法: ClickOnce を使用して、複数バージョンの .NET Framework で実行できるアプリケーションを展開する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, multiple .NET Framework versions
- ClickOnce deployment, multiple .NET Framework versions
- deploying applications [ClickOnce], multiple .NET Framework versions
ms.assetid: e0a8c330-21bc-4eb2-b936-fd0f3c3221f1
caps.latest.revision: "17"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: d634d320df50dafc203ea1b1b4c8366ae3e24a41
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-use-clickonce-to-deploy-applications-that-can-run-on-multiple-versions-of-the-net-framework"></a>方法: ClickOnce を使用して、複数のバージョンの .NET Framework で実行できるアプリケーションを配置する
ClickOnce の配置テクノロジを使用して複数のバージョンの .NET Framework を対象とするアプリケーションを展開することができます。 これは、生成して、アプリケーション マニフェストと配置マニフェストを更新する必要があります。  
  
> [!NOTE]
>  複数バージョンの .NET Framework を対象とするアプリケーションを変更すると、前に、複数バージョンの .NET Framework を使用して、アプリケーションが実行を確認する必要があります。 バージョンの共通言語ランタイムが異なる[!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)]と .NET Framework 2.0、.NET Framework 3.0、および .NET Framework 3.5 とします。  
  
 このプロセスでは、次の手順が必要です。  
  
1.  アプリケーション マニフェストと配置マニフェストを生成します。  
  
2.  複数の .NET Framework のバージョンを一覧表示する、配置マニフェストを変更します。  
  
3.  互換性のある .NET Framework ランタイム バージョンを一覧表示、app.config ファイルを変更します。  
  
4.  .NET Framework アセンブリと依存アセンブリをマークする、アプリケーション マニフェストを変更します。  
  
5.  アプリケーション マニフェストに署名します。  
  
6.  更新し、配置マニフェストに署名します。  
  
### <a name="to-generate-the-application-and-deployment-manifests"></a>アプリケーション マニフェストと配置マニフェストを生成するには  
  
-   発行ウィザード、または、プロジェクト デザイナーの [発行] ページを使用してアプリケーションを発行し、アプリケーション マニフェストと配置マニフェスト ファイルを生成します。 詳細については、次を参照してください。[する方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)または[発行 ページ、プロジェクト デザイナー](../ide/reference/publish-page-project-designer.md)です。  
  
### <a name="to-change-the-deployment-manifest-to-list-the-multiple-net-framework-versions"></a>複数の .NET Framework のバージョンを一覧表示する、配置マニフェストを変更するには  
  
1.  発行ディレクトリでは、Visual Studio で、XML エディターを使用して、配置マニフェストを開きます。 配置マニフェストには、.application ファイル名拡張子が付きます。  
  
2.  間の XML コードを置き換える、`<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">`と`</compatibleFrameworks>`アプリケーションをサポートする .NET Framework バージョンを一覧表示する xml 要素です。  
  
     次の表は、使用可能な .NET Framework のバージョンと対応する XML が配置マニフェストに追加することができますがの一部を示します。  
  
    |.NET Framework のバージョン|XML|  
    |----------------------------|---------|  
    |4 つのクライアント|\<framework targetVersion =「4.0」プロファイル「クライアント」supportedRuntime を = =「4.0.30319」/>|  
    |4 のフル|\<framework targetVersion =「4.0」プロファイル"Full"supportedRuntime を = =「4.0.30319」/>|  
    |3.5 クライアント|\<framework targetVersion =「3.5」プロファイル「クライアント」supportedRuntime を = =「2.0.50727」/>|  
    |3.5 完全|\<framework targetVersion =「3.5」プロファイル"Full"supportedRuntime を = =「2.0.50727」/>|  
    |3.0|\<framework targetVersion「3.0」supportedRuntime を = =「2.0.50727」/>|  
  
### <a name="to-change-the-appconfig-file-to-list-the-compatible-net-framework-runtime-versions"></a>App.config ファイルを互換性のある .NET Framework ランタイムのバージョンを一覧表示を変更するには  
  
1.  ソリューション エクスプ ローラーでは、Visual Studio で、XML エディターを使用して、App.config ファイルを開きます。  
  
2.  置換 (追加)、XML コードの間、`<startup>`と`</startup>`アプリケーションのサポートされている .NET Framework ランタイムの一覧を表示する xml 要素です。  
  
     次の表は、使用可能な .NET Framework のバージョンと対応する XML が配置マニフェストに追加することができますがの一部を示します。  
  
    |.NET framework ランタイムのバージョン|XML|  
    |------------------------------------|---------|  
    |4 つのクライアント|\<supportedRuntime バージョン"v4.0.30319"sku を = ="です。NETFramework、バージョン v4.0、プロファイルを = = Client"/>|  
    |4 のフル|\<supportedRuntime バージョン"v4.0.30319"sku を = ="です。NETFramework, Version = v4.0"/>|  
    |3.5 完全|\<supportedRuntime version="v2.0.50727"/ >|  
    |3.5 クライアント|\<supportedRuntime バージョン"v2.0.50727"sku を = =「クライアント」/>|  
  
### <a name="to-change-the-application-manifest-to-mark-dependent-assemblies-as-net-framework-assemblies"></a>.NET Framework アセンブリと依存アセンブリをマークする、アプリケーション マニフェストを変更するには  
  
1.  発行ディレクトリでは、Visual Studio で、XML エディターを使用して、アプリケーション マニフェストを開きます。 配置マニフェストには、.manifest ファイル名拡張子が付きます。  
  
2.  追加`group="framework"`sentinel アセンブリの依存関係に XML を (`System.Core`、 `WindowsBase`、 `Sentinel.v3.5Client`、および`System.Data.Entity`)。 たとえば、XML の場合は、次のようになります。  
  
    ```  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">  
    ```  
  
3.  更新プログラムのバージョン番号、 `<assemblyIdentity>` Microsoft.Windows.CommonLanguageRuntime の最小の共通部分は、.NET Framework のバージョン番号の要素。 たとえば、アプリケーションが .NET Framework 3.5 を対象とする場合と[!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)]使用、2.0.50727.0 バージョン番号と、XML、次のようになります。  
  
    ```  
    <dependency>  
      <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
        <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />  
      </dependentAssembly>  
    </dependency>  
    ```  
  
### <a name="to-update-and-re-sign-the-application-and-deployment-manifests"></a>マニフェストを更新して、アプリケーションおよび配置を再署名  
  
-   更新し、アプリケーション マニフェストと配置マニフェストに再署名します。 詳細については、次を参照してください。[する方法: 再署名アプリケーション マニフェストと配置マニフェスト](../deployment/how-to-re-sign-application-and-deployment-manifests.md)です。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [\<compatibleFrameworks > 要素](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [\<依存関係 > 要素](../deployment/dependency-element-clickonce-application.md)   
 [ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)   
 [構成ファイル スキーマ](/dotnet/framework/configure-apps/file-schema/index)