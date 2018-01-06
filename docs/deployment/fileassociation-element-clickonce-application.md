---
title: "&lt;fileAssociation&gt;要素 (ClickOnce アプリケーション) |Microsoft ドキュメント"
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
- <fileAssociation> element [ClickOnce application manifest]
- manifests [ClickOnce], fileAssociation element
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
caps.latest.revision: "8"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: bd5d7ed1a37923cefc4a6b7975610b6016fd0ae6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltfileassociationgt-element-clickonce-application"></a>&lt;fileAssociation&gt;要素 (ClickOnce アプリケーション)
アプリケーションに関連付けるファイル拡張子を識別します。  
  
## <a name="syntax"></a>構文  
  
```  
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
|`extension`|必須。 アプリケーションに関連付けるファイル拡張子。|  
|`description`|必須。 シェルで使用するため、ファイルの種類の説明です。|  
|`progid`|必須。 ファイルの種類を一意に識別する名前です。|  
|`defaultIcon`|必須。 この拡張機能を持つファイルを使用するアイコンを指定します。 使用してアイコン ファイルを指定する必要があります、 [\<ファイル > 要素](../deployment/file-element-clickonce-application.md)内で、 [\<アセンブリ > 要素](../deployment/assembly-element-clickonce-application.md)この要素を格納しています。|  
  
## <a name="remarks"></a>コメント  
 この要素は、XML 名前空間参照を含める必要があります"urn: スキーマ-microsoft-com:clickonce.v1"です。 場合、`<fileAssociation>`要素を使用すると、後に続く必要がありますが、`<application>`では親要素[\<アセンブリ > 要素](../deployment/assembly-element-clickonce-application.md)です。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]既存のファイルの関連付けは上書きされません。 ただし、ClickOnce アプリケーションでは、現在のユーザーのみのファイル拡張子を上書きできます。 ClickOnce アプリケーションをアンインストールしたら、ClickOnce は、ユーザーのファイルの関連付けを削除し、コンピューターごとの関連付けが再度アクティブです。  
  
## <a name="example"></a>例  
 次のコード例を示しています`fileAssociation`アプリケーション内の要素を使用して展開されているテキスト エディターのアプリケーションのマニフェストの[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]します。 このコード例も含まれています、 [\<ファイル > 要素](../deployment/file-element-clickonce-application.md)で必要な`defaultIcon`属性。  
  
```  
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
  
## <a name="see-also"></a>参照  
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)