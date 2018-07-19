---
title: '&lt;fileAssociation&gt;要素 (ClickOnce アプリケーション) |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <fileAssociation> element [ClickOnce application manifest]
- manifests [ClickOnce], fileAssociation element
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 62e099f949af3cc3ea336663224c1dd92726ac53
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080026"
---
# <a name="ltfileassociationgt-element-clickonce-application"></a>&lt;fileAssociation&gt;要素 (ClickOnce アプリケーション)
アプリケーションに関連するファイル拡張子を識別します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<fileAssociation  
    xmlns="urn:schemas-microsoft-com:clickonce.v1"  
    extension  
    description  
    progid  
    defaultIcon  
/>  
```  
  
## <a name="elements-and-attributes"></a>要素と属性  
 `fileAssociation` 要素は省略可能です。 要素には、次の属性があります。  
  
|属性|説明|  
|---------------|-----------------|  
|`extension`|必須。 アプリケーションに関連するファイル拡張子。|  
|`description`|必須。 シェルによって使用されるファイルの種類の説明。|  
|`progid`|必須。 ファイルの種類を一意に識別する名前。|  
|`defaultIcon`|必須。 この拡張機能でファイルを使用するアイコンを指定します。 使用してアイコン ファイルを指定する必要があります、 [\<ファイル > 要素](../deployment/file-element-clickonce-application.md)内、 [\<アセンブリ > 要素](../deployment/assembly-element-clickonce-application.md)この要素を格納しています。|  
  
## <a name="remarks"></a>Remarks  
 この要素への XML 名前空間参照を含める必要があります"urn: スキーマ-microsoft-com:clickonce.v1"。 場合、`<fileAssociation>`要素を使用して、後に、必要があります、`<application>`では親要素[\<アセンブリ > 要素](../deployment/assembly-element-clickonce-application.md)します。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 既存のファイルの関連付けは上書きされません。 ただし、ClickOnce アプリケーションでは、現在のユーザーのみのファイル拡張子を上書きできます。 ClickOnce アプリケーションをアンインストールすると後、ClickOnce は、ユーザーのファイルの関連付けを削除し、コンピューターごとの関連付けがもう一度アクティブです。  
  
## <a name="example"></a>例  
 次のコード例を示しています`fileAssociation`テキスト エディター アプリケーションを使用してデプロイ用のマニフェストをアプリケーション内の要素[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]します。 このコード例も含まれています、 [\<ファイル > 要素](../deployment/file-element-clickonce-application.md)によって必要な`defaultIcon`属性。  
  
```xml  
<file name="text.ico" size="4286">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>0joAqhmfeBb93ZneZv/oTMP2brY=</dsig:DigestValue>  
  </hash>  
</file>  
<file name="writing.ico" size="9662">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>2cL2U7cm13nG40v9MQdxYKazIwI=</dsig:DigestValue>  
  </hash>  
</file>  
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".text" description="Text  Document (ClickOnce)" progid="Text.Document" defaultIcon="text.ico" />  
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".writing" description="Writings (ClickOnce)" progid="Writing.Document" defaultIcon="writing.ico" />  
```  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)