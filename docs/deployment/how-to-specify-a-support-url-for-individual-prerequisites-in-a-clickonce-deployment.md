---
title: "方法 : ClickOnce 配置で個々の必要条件にサポート URL を指定する | Microsoft Docs"
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
  - "ClickOnce 配置, 必要条件"
  - "ClickOnce 配置, URL"
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 方法 : ClickOnce 配置で個々の必要条件にサポート URL を指定する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] の配置によって、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションを実行するためにクライアント コンピューターに必要な数々の必須コンポーネントを調べることができます。  たとえば、最低限必要な [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] のバージョン、オペレーティング システムのバージョン、およびグローバル アセンブリ キャッシュ \(GAC\) に事前にインストールしておく必要があるアセンブリなどです。  ただし、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ではその必須コンポーネント自体をインストールすることができません。必須コンポーネントが見つかった場合、インストールを停止し、インストールが失敗した理由を説明するダイアログ ボックスを表示するのみです。  
  
 必要条件をインストールするには 2 つの方法があります。  ブートストラップ アプリケーションを使用してインストールできます。  または、個々の必要条件に対してサポート URL を指定します。この URL は、必要条件が見つからなかった場合にダイアログ ボックスでユーザーに表示されます。  この URL で参照されるページには、必要条件をインストールするための手順へのリンクが含まれている可能性があります。  個々の必要条件に対するサポート URL がアプリケーションで指定されない場合は、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] によって、アプリケーション全体の配置マニフェストで指定されているサポート URL \(定義されている場合\) が表示されます。  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、Mage.exe、および MageUI.exe は、いずれも [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 配置を生成するために使用できますが、どのツールも個々の必要条件に対するサポート URL の指定は直接サポートしていません。  ここでは、これらのサポート URL を組み込むように、配置のアプリケーション マニフェストおよび配置マニフェストを変更する方法について説明します。  
  
### 個々の必要条件に対するサポート URL の指定  
  
1.  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションのアプリケーション マニフェスト \(.manifest ファイル\) をテキスト エディターで開きます。  
  
2.  オペレーティング システムの必要条件に関しては、`supportUrl` 属性を `dependentOS` 要素に追加します。  
  
    ```  
     <dependency>  
        <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
          <osVersionInfo>  
            <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
          </osVersionInfo>  
        </dependentOS>  
      </dependency>  
    ```  
  
3.  共通言語ランタイムのある特定のバージョンに対する必要条件の場合は、`supportUrl` 属性を、共通言語ランタイムの依存関係を指定する `dependentAssembly` エントリに追加します。  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
          <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
4.  グローバル アセンブリ キャッシュにプレインストールする必要があるアセンブリに対する必要条件に関しては、必要なアセンブリを指定する `dependentAssembly` 要素に `supportUrl` を設定します。  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
          <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
5.  省略可能です。  .NET Framework 4 を対象とするアプリケーションの場合、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションの配置マニフェスト \(.application ファイル\) をテキスト エディターで開きます。  
  
6.  .NET Framework 4 の必要条件に関しては、`supportUrl` 属性を `compatibleFrameworks` 要素に追加します。  
  
    ```  
    <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
      <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
      <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
    </compatibleFrameworks>  
    ```  
  
7.  アプリケーション マニフェストを手動で変更した後に、デジタル証明書を使用してアプリケーション マニフェストに再署名し、さらに配置マニフェストも更新および再署名する必要があります。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] を使用してこれらのファイルを再生成すると手動での変更が消去されるため、この作業には Mage.exe または MageUI.exe の SDK ツールを使用する必要があります。  Mage.exe を使用したマニフェストへの再署名の詳細については、「[方法: アプリケーション マニフェストおよび配置マニフェストに再署名する](../deployment/how-to-re-sign-application-and-deployment-manifests.md)」を参照してください。  
  
## .NET Framework セキュリティ  
 アプリケーションが部分信頼で実行するようにマークされている場合は、ダイアログ ボックスにサポート URL が表示されません。  
  
## 参照  
 [Mage.exe \(マニフェストの生成および編集ツール\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [チュートリアル : ClickOnce アプリケーションを手動で配置する](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [\<compatibleFrameworks\> 要素](../Topic/%3CcompatibleFrameworks%3E%20Element%20\(ClickOnce%20Deployment\).md)   
 [ClickOnce と Authenticode](../deployment/clickonce-and-authenticode.md)   
 [アプリケーション配置の必要条件](../deployment/application-deployment-prerequisites.md)