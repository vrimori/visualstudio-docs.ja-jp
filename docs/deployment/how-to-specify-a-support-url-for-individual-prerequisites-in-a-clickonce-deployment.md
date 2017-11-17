---
title: "方法: ClickOnce の配置における個別の前提条件のサポート URL の指定 |Microsoft ドキュメント"
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
- ClickOnce deployment, prerequisites
- ClickOnce deployment, URLs
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
caps.latest.revision: "10"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 2335c0279c8e7a23e1b514a8264651e73fedebfc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>方法 : ClickOnce 配置で個々の必要条件にサポート URL を指定する
A[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]数のクライアント コンピューターで使用する必要がある前提条件の展開をテストできます、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションを実行します。 必要な最小バージョンが含まれます、 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]、オペレーティング システム、およびグローバル アセンブリ キャッシュ (GAC) がプレインストールされている必要があるすべてのアセンブリのバージョン。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]、ただし、インストールできませんこれらの前提条件のいずれかの自体です。前提条件が見つからない場合、インストールを中止し、インストールが失敗した理由を説明するダイアログ ボックスが表示されます。  
  
 前提条件をインストールするための 2 つの方法があります。 ブートス トラップ アプリケーションを使用してこれらをインストールすることができます。 または、前提条件が見つからない場合は、ダイアログ ボックスのユーザーに表示する個別の前提条件のサポートの URL を指定することができます。 この URL で参照されているページは、必須の前提条件をインストールするための手順へのリンクを含めることができます。 アプリケーションで個々 の必要条件に対するサポート URL が指定されていない場合[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]が定義されている場合、全体として、アプリケーションの配置マニフェストで指定されたサポート URL が表示されます。  
  
 中に[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、Mage.exe および MageUI.exe すべて使用できますを生成する[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]展開では、これらのツールを直接サポートする個別の前提条件に関するサポート URL を指定します。 このドキュメントは、の展開を変更する方法を説明アプリケーション マニフェストと配置マニフェストに含まれる Url をサポートします。  
  
### <a name="specifying-a-support-url-for-an-individual-prerequisite"></a>個々 の必要条件に対するサポート URL の指定  
  
1.  アプリケーション マニフェスト (.manifest ファイル) を開き、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]をテキスト エディターでアプリケーションです。  
  
2.  オペレーティング システムの前提条件、追加、`supportUrl`属性を`dependentOS`要素。  
  
    ```  
     <dependency>  
        <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
          <osVersionInfo>  
            <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
          </osVersionInfo>  
        </dependentOS>  
      </dependency>  
    ```  
  
3.  共通言語ランタイムの特定のバージョンの前提条件、追加、`supportUrl`属性を`dependentAssembly`共通言語ランタイムの依存関係を指定するエントリ。  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
          <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
4.  アセンブリをグローバル アセンブリ キャッシュがプレインストールされている必要がありますの前提条件、設定、`supportUrl`の`dependentAssembly`必要なアセンブリを指定する要素。  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
          <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
5.  省略可能です。 .NET Framework 4 を対象とするアプリケーションの配置マニフェスト (.application ファイル) を開いて、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]をテキスト エディターでアプリケーションです。  
  
6.  .NET Framework 4 の前提条件、追加、`supportUrl`属性を`compatibleFrameworks`要素。  
  
    ```  
    <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
      <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
      <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
    </compatibleFrameworks>  
    ```  
  
7.  アプリケーション マニフェストを手動で変更した後、デジタル証明書を使用してアプリケーション マニフェストに再署名し、更新しても、配置マニフェストに再署名します。 Mage.exe を使用する必要がありますかを使用してこれらのファイルを再生成すると、このタスクを実行するツールの MageUI.exe SDK[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]手動の変更内容を消去します。 Mage.exe を使用してマニフェストに再署名する方法の詳細については、次を参照してください。[する方法: 再署名アプリケーション マニフェストと配置マニフェスト](../deployment/how-to-re-sign-application-and-deployment-manifests.md)です。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 サポート URL は、部分信頼で実行するアプリケーションがマークされている場合、ダイアログ ボックスでは表示されません。  
  
## <a name="see-also"></a>関連項目  
 [Mage.exe (マニフェストの生成および編集ツール)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [チュートリアル : ClickOnce アプリケーションを手動で配置する](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [\<compatibleFrameworks > 要素](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [ClickOnce と Authenticode](../deployment/clickonce-and-authenticode.md)   
 [アプリケーション配置の必要条件](../deployment/application-deployment-prerequisites.md)