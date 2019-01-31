---
title: ClickOnce アプリケーション マニフェスト |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- application manifests [ClickOnce]
- ClickOnce, application manifests
ms.assetid: 29570cec-4e53-4660-a850-abc4fa150243
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 47c3ca0877500e8242e7fb96ba15b19c9d8a6e13
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54916991"
---
# <a name="clickonce-application-manifest"></a>ClickOnce アプリケーション マニフェスト
A[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション マニフェストを使用して展開されているアプリケーションを記述する XML ファイルは、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]します。  

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーション マニフェストは、次の要素と属性があります。  


| 要素 | 説明 | 属性 |
| - | - | - |
| [\<アセンブリ > 要素](../deployment/assembly-element-clickonce-application.md) | 必須です。 最上位の要素です。 | `manifestVersion` |
| [\<assemblyIdentity > 要素](../deployment/assemblyidentity-element-clickonce-application.md) | 必須です。 プライマリ アセンブリを識別、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション。 | `name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `language` |
| [\<trustInfo > 要素](../deployment/trustinfo-element-clickonce-application.md) | アプリケーションのセキュリティ要件を識別します。 | なし |
| [\<entryPoint > 要素](../deployment/entrypoint-element-clickonce-application.md) | 必須です。 アプリケーション コードのエントリ ポイントを識別します。 | `name` |
| [\<依存関係 > 要素](../deployment/dependency-element-clickonce-application.md) | 必須です。 アプリケーションを実行するために必要な依存関係をそれぞれ識別します。 任意で、プレインストールする必要のあるアセンブリを識別します。 | なし |
| [\<file> 要素](../deployment/file-element-clickonce-application.md) | 任意。 アプリケーションで使用される各非アセンブリ ファイルを識別します。 ファイルに関連付けられているコンポーネント オブジェクト モデル (COM) 分離データを含めることができます。 | `name`<br /><br /> `size`<br /><br /> `group`<br /><br /> `optional`<br /><br /> `writeableType` |
| [\<fileAssociation > 要素](../deployment/fileassociation-element-clickonce-application.md) | 任意。 アプリケーションに関連するファイル拡張子を識別します。 | `extension`<br /><br /> `description`<br /><br /> `progid`<br /><br /> `defaultIcon` |

## <a name="remarks"></a>コメント  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション マニフェスト ファイルを使用してデプロイされたアプリケーションを識別する[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]します。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] の詳細については、「[ClickOnce のセキュリティと配置](../deployment/clickonce-security-and-deployment.md)」を参照してください。  

## <a name="file-location"></a>ファイルの場所  
 A[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション マニフェストは、展開の 1 つのバージョンを特定します。 このため、保存するとは別に配置マニフェストとします。 通常は、関連付けられているバージョンにちなんだ名前のサブディレクトリ内に配置します。  

 アプリケーション マニフェストは、展開する前に常に署名する必要があります。 使用する必要がある場合は、アプリケーション マニフェストを手動で変更すると、 *mage.exe*アプリケーション マニフェストに再署名、配置マニフェストを更新し、配置マニフェストを再署名します。 詳細については、「[チュートリアル:ClickOnce アプリケーションを手動で展開](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)します。  

## <a name="file-name-syntax"></a>ファイル名の構文  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーション マニフェスト ファイルの名前は、`assemblyIdentity` 要素に指定されたアプリケーションの完全名と拡張子に、*.manifest* という拡張子を付けたものにします。 たとえば、参照するアプリケーション マニフェスト、 *Example.exe*アプリケーションでは、次のファイル名構文を使用します。  

 `example.exe.manifest`  

## <a name="example"></a>例  
 次のコード例のアプリケーション マニフェストを示しています、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション。  

```xml
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
...  
</Signature></r:issuer></r:license></msrel:RelData></KeyInfo></Signature></asmv1:assembly>  
```  

## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)
