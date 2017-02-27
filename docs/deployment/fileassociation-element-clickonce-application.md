---
title: "&lt;fileAssociation&gt; 要素 (ClickOnce アプリケーション) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "<fileAssociation> 要素 [ClickOnce アプリケーション マニフェスト]"
  - "マニフェスト [ClickOnce], fileAssociation 要素"
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 8
---
# &lt;fileAssociation&gt; 要素 (ClickOnce アプリケーション)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

アプリケーションに関連付ける拡張子を指定します。  
  
## 構文  
  
```  
<fileAssociation  
    xmlns="urn:schemas-microsoft-com:clickonce.v1"  
    extension  
    description  
    progid  
    defaultIcon  
/>  
```  
  
## 要素と属性  
 `fileAssociation` 要素は省略可能です。  この要素には、次の属性があります。  
  
|属性|Description|  
|--------|-----------------|  
|`extension`|必ず指定します。  アプリケーションに関連付ける拡張子を指定します。|  
|`description`|必ず指定します。  ファイルの種類の説明です。シェルで使用されます。|  
|`progid`|必ず指定します。  ファイルの種類を一意に識別する名前です。|  
|`defaultIcon`|必ず指定します。  この拡張子を持つファイルに使用するアイコンを指定します。  アイコン ファイルは、この要素が存在する [\<assembly\> 要素](../deployment/assembly-element-clickonce-application.md)内に、[\<file\> 要素](../Topic/%3Cfile%3E%20Element%20\(ClickOnce%20Application\).md)を使って指定する必要があります。|  
  
## 解説  
 この要素は、"urn:schemas\-microsoft\-com:clickonce.v1" の XML 名前空間参照を含んでいる必要があります。  使用する場合、`<fileAssociation>` 要素は、親 [\<assembly\> 要素](../deployment/assembly-element-clickonce-application.md)内の `<application>` 要素の後に記述する必要があります。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] では、既存のファイルの関連付けは上書きされません。  ただし、ClickOnce アプリケーションは現在のユーザーのファイル拡張子のみオーバーライドできます。  その ClickOnce アプリケーションをアンインストールすると、ユーザーのファイルの関連付けが削除され、コンピューターごとの関連付けが再びアクティブになります。  
  
## 使用例  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] を使用して配置されるテキスト エディター アプリケーションの、アプリケーション マニフェスト内の `fileAssociation` 要素を示すコード例を次に示します。  このコード例には、`defaultIcon` 属性に必要な [\<file\> 要素](../Topic/%3Cfile%3E%20Element%20\(ClickOnce%20Application\).md)も含まれています。  
  
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
  
## 参照  
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)