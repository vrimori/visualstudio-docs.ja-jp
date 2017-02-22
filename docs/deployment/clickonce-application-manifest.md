---
title: "ClickOnce アプリケーション マニフェスト | Microsoft Docs"
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
  - "アプリケーション マニフェスト [ClickOnce]"
  - "ClickOnce, アプリケーション マニフェスト"
ms.assetid: 29570cec-4e53-4660-a850-abc4fa150243
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ClickOnce アプリケーション マニフェスト
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] のアプリケーション マニフェストは [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]を使用して配置されるアプリケーションを記述する XML ファイルです。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] の アプリケーション マニフェストには次の要素と属性があります。  
  
|要素|Description|属性|  
|--------|-----------------|--------|  
|[\<assembly\> 要素](../deployment/assembly-element-clickonce-application.md)|必ず指定します。  最上位の要素です。|`manifestVersion`|  
|[\<assemblyIdentity\> 要素](../deployment/assemblyidentity-element-clickonce-application.md)|必ず指定します。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションのプライマリ アセンブリを指定します。|`name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `language`|  
|[\<trustInfo\> 要素](../deployment/trustinfo-element-clickonce-application.md)|アプリケーションのセキュリティ要件を指定します。|なし|  
|[\<entryPoint\> 要素](../deployment/entrypoint-element-clickonce-application.md)|必ず指定します。  アプリケーション コードのエントリ ポイントを指定します。|`name`|  
|[\<dependency\> 要素](../deployment/dependency-element-clickonce-application.md)|必ず指定します。  アプリケーションを実行するために必要な依存関係をそれぞれ指定します。  必要な場合には、プレインストールしなければならないアセンブリを指定します。|なし|  
|[\<file\> 要素](../Topic/%3Cfile%3E%20Element%20\(ClickOnce%20Application\).md)|省略可能です。  アプリケーションで使用する、アセンブリ以外のファイルを指定します。  ファイルに関連付けられている分離COM \(Component Object Model\) コンポーネントを含めることができます。|`name`<br /><br /> `size`<br /><br /> `group`<br /><br /> `optional`<br /><br /> `writeableType`|  
|[\<fileAssociation\> 要素](../deployment/fileassociation-element-clickonce-application.md)|省略可能です。  アプリケーションに関連付ける拡張子を指定します。|`extension`<br /><br /> `description`<br /><br /> `progid`<br /><br /> `defaultIcon`|  
  
## 解説  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] のアプリケーション マニフェスト ファイルは [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]を使用して配置されるアプリケーションを指定します。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] の詳細については、「[ClickOnce のセキュリティと配置](../deployment/clickonce-security-and-deployment.md)」を参照してください。  
  
## ファイルの場所  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] のアプリケーション マニフェストは、配置の一つのバージョンに固有です。  したがって、配置マニフェストとは別に保存する必要があります。  通常は、関連付けられたバージョンに合わせた名前を付けたサブディレクトリに格納します。  
  
 アプリケーション マニフェストには、配置する前に署名する必要があります。  アプリケーション マニフェストを手動で変更した場合は、mage.exe を使用して、アプリケーション マニフェストに再署名し、配置マニフェストを更新してから、配置マニフェストに再署名する必要があります。  詳細については、「[チュートリアル : ClickOnce アプリケーションを手動で配置する](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)」を参照してください。  
  
## ファイル名の構文  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] のアプリケーション マニフェスト ファイルの名前に拡張子 .manifest が続く `assemblyIdentity` の要素に指定されたアプリケーションの完全名と拡張子にする必要があります。  たとえば、Example.exe アプリケーションを参照するアプリケーション マニフェストでは、次のファイル名を使用します。  
  
 `example.exe.manifest`  
  
## 使用例  
 次のコード例は、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションのアプリケーション マニフェストを示しています。  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<asmv1:assembly xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd" manifestVersion="1.0" xmlns:asmv3="urn:schemas-microsoft-com:asm.v3" xmlns:dsig="http://www.w3.org/2000/09/xmldsig#" xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2" xmlns="urn:schemas-microsoft-com:asm.v2" xmlns:asmv1="urn:schemas-microsoft-com:asm.v1" xmlns:asmv2="urn:schemas-microsoft-com:asm.v2" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">  
  <asmv1:assemblyIdentity name="My Application Deployment.exe" version="1.0.0.0" publicKeyToken="43cb1e8e7a352766" language="neutral" processorArchitecture="x86" type="win32" />  
  <application />  
  <entryPoint>  
    <assemblyIdentity name="MyApplication" version="1.0.0.0" language="neutral" processorArchitecture="x86" />  
    <commandLine file="MyApplication.exe" parameters="" />  
  </entryPoint>  
  <trustInfo>  
    <security>  
      <applicationRequestMinimum>  
        <PermissionSet Unrestricted="true" ID="Custom" SameSite="site" />  
        <defaultAssemblyRequest permissionSetReference="Custom" />  
      </applicationRequestMinimum>  
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">  
        <!--  
          UAC Manifest Options  
          If you want to change the Windows User Account Control level replace the   
          requestedExecutionLevel node with one of the following.  
  
        <requestedExecutionLevel  level="asInvoker" uiAccess="false" />  
        <requestedExecutionLevel  level="requireAdministrator" uiAccess="false" />  
        <requestedExecutionLevel  level="highestAvailable" uiAccess="false" />  
  
         If you want to utilize File and Registry Virtualization for backward   
         compatibility then delete the requestedExecutionLevel node.  
    -->  
        <requestedExecutionLevel level="asInvoker" uiAccess="false" />  
      </requestedPrivileges>  
    </security>  
  </trustInfo>  
  <dependency>  
    <dependentOS>  
      <osVersionInfo>  
        <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
      </osVersionInfo>  
    </dependentOS>  
  </dependency>  
  <dependency>  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
      <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.20506.0" />  
    </dependentAssembly>  
  </dependency>  
  <dependency>  
    <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="4096">  
      <assemblyIdentity name="MyApplication" version="1.0.0.0" language="neutral" processorArchitecture="x86" />  
      <hash>  
        <dsig:Transforms>  
          <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
        </dsig:Transforms>  
        <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
        <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>  
      </hash>  
    </dependentAssembly>  
  </dependency>  
<publisherIdentity name="CN=DOMAINCONTROLLER\UserMe" issuerKeyHash="18312a18a21b215ecf4cdb20f5a0e0b0dd263c08" /><Signature Id="StrongNameSignature" xmlns="http://www.w3.org/2000/09/xmldsig#">  
…  
</Signature></r:issuer></r:license></msrel:RelData></KeyInfo></Signature></asmv1:assembly>  
```  
  
## 参照  
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)