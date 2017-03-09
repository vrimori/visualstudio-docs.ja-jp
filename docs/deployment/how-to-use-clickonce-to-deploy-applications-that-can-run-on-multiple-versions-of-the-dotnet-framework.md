---
title: "方法: ClickOnce を使用して、複数のバージョンの .NET Framework で実行できるアプリケーションを配置する | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce アプリケーション, 複数のバージョンの .NET Framework"
  - "ClickOnce 配置, 複数のバージョンの .NET Framework"
  - "配置 (アプリケーションを) [ClickOnce], 複数のバージョンの .NET Framework"
ms.assetid: e0a8c330-21bc-4eb2-b936-fd0f3c3221f1
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 方法: ClickOnce を使用して、複数のバージョンの .NET Framework で実行できるアプリケーションを配置する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ClickOnce 配置テクノロジを使用すると、複数のバージョンの .NET Framework を対象とするアプリケーションを配置できます。  これには、アプリケーション マニフェストと配置マニフェストを生成して更新する必要があります。  
  
> [!NOTE]
>  複数のバージョンの .NET Framework を対象とするようにアプリケーションを変更する前に、そのアプリケーションが .NET Framework の複数のバージョンで動作することを確認する必要があります。  該当バージョンの共通言語ランタイムは、[!INCLUDE[net_v40_short](../debugger/includes/net_v40_short_md.md)] と .NET Framework 2.0、.NET Framework 3.0、.NET Framework 3.5 とで異なります。  
  
 このプロセスは、次の手順で実行します。  
  
1.  アプリケーション マニフェストと配置マニフェストを生成します。  
  
2.  アプリケーション マニフェストを変更して、複数のバージョンの .NET Framework を指定します。  
  
3.  app.config ファイルを変更して、互換性のある .NET Framework ランタイム バージョンを指定します。  
  
4.  アプリケーション マニフェストを変更して、依存アセンブリを .NET Framework アセンブリとして指定します。  
  
5.  アプリケーション マニフェストに署名します。  
  
6.  配置マニフェストを更新し、配置マニフェストに署名します。  
  
### アプリケーション マニフェストと配置マニフェストを生成するには  
  
-   発行ウィザード、またはプロジェクト デザイナーの \[発行\] ページを使用して、アプリケーションを発行し、アプリケーション マニフェストと配置マニフェストのファイルを生成します。  詳細については、「[方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)」または「[\[発行\] ページ \(プロジェクト デザイナー\)](../Topic/Publish%20Page,%20Project%20Designer.md)」を参照してください。  
  
### アプリケーション マニフェストを変更して、複数のバージョンの .NET Framework を指定するには  
  
1.  publish ディレクトリで、Visual Studio の XML エディターを使用して配置マニフェストを開きます。  配置マニフェストのファイル名拡張子は .application です。  
  
2.  `<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">` 要素と `</compatibleFrameworks>` 要素の間にある XML コードを、アプリケーションでサポートする .NET Framework のバージョンを指定する XML に置き換えます。  
  
     次の表に、使用可能な .NET Framework のバージョンの一部と、対応する XML を示します。これらの XML は配置マニフェストに追加できます。  
  
    |.NET Framework のバージョン|XML|  
    |---------------------------|---------|  
    |4 Client|\<framework targetVersion\="4.0" profile\="Client" supportedRuntime\="4.0.30319" \/\>|  
    |4 Full|\<framework targetVersion\="4.0" profile\="Full" supportedRuntime\="4.0.30319" \/\>|  
    |3.5 Client|\<framework targetVersion\="3.5" profile\="Client" supportedRuntime\="2.0.50727" \/\>|  
    |3.5 Full|\<framework targetVersion\="3.5" profile\="Full" supportedRuntime\="2.0.50727" \/\>|  
    |3.0|\<framework targetVersion\="3.0" supportedRuntime\="2.0.50727" \/\>|  
  
### app.config ファイルを変更して、互換性のある .NET Framework ランタイム バージョンを指定するには  
  
1.  ソリューション エクスプローラーで、Visual Studio の XML エディターを使用して App.config ファイルを開きます。  
  
2.  `<startup>` 要素と `</startup>` 要素の間にある XML コードを、アプリケーションでサポートする .NET Framework ランタイムを指定する XML に置き換えます \(または XML コードを追加します\)。  
  
     次の表に、使用可能な .NET Framework のバージョンの一部と、対応する XML を示します。これらの XML は配置マニフェストに追加できます。  
  
    |.NET Framework ランタイムのバージョン|XML|  
    |--------------------------------|---------|  
    |4 Client|\<supportedRuntime version\="v4.0.30319" sku\=".NETFramework,Version\=v4.0,Profile\=Client" \/\>|  
    |4 Full|\<supportedRuntime version\="v4.0.30319" sku\=".NETFramework,Version\=v4.0" \/\>|  
    |3.5 Full|\<supportedRuntime version\="v2.0.50727"\/\>|  
    |3.5 Client|\<supportedRuntime version\="v2.0.50727" sku\="Client"\/\>|  
  
### アプリケーション マニフェストを変更して、依存アセンブリを .NET Framework アセンブリとして指定するには  
  
1.  publish ディレクトリで、Visual Studio の XML エディターを使用してアプリケーション マニフェストを開きます。  アプリケーション マニフェストのファイル名拡張子は .manifest です。  
  
2.  センティネル アセンブリ \(`System.Core`、`WindowsBase`、`Sentinel.v3.5Client`、および `System.Data.Entity`\) の依存関係を示す XML に `group="framework"` を追加します。  XML は、次の例のようになります。  
  
    ```  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">  
    ```  
  
3.  Microsoft.Windows.CommonLanguageRuntime の `<assemblyIdentity>` 要素のバージョン番号を、対象とする .NET Framework のうち最低のバージョン番号に更新します。  たとえば、.NET Framework 3.5 と [!INCLUDE[net_v40_short](../debugger/includes/net_v40_short_md.md)] をアプリケーションで対象とする場合は、バージョン番号 2.0.50727.0 を使用します。XML は、次のようになります。  
  
    ```  
    <dependency>  
      <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
        <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />  
      </dependentAssembly>  
    </dependency>  
    ```  
  
### アプリケーション マニフェストと配置マニフェストを更新し、それらに再署名するには  
  
-   アプリケーション マニフェストと配置マニフェストを更新し、それらに再署名します。  詳細については、「[方法: アプリケーション マニフェストおよび配置マニフェストに再署名する](../deployment/how-to-re-sign-application-and-deployment-manifests.md)」を参照してください。  
  
## 参照  
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [\<compatibleFrameworks\> 要素](../Topic/%3CcompatibleFrameworks%3E%20Element%20\(ClickOnce%20Deployment\).md)   
 [\<dependency\> 要素](../deployment/dependency-element-clickonce-application.md)   
 [ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)   
 [構成ファイル スキーマ](../Topic/Configuration%20File%20Schema%20for%20the%20.NET%20Framework.md)