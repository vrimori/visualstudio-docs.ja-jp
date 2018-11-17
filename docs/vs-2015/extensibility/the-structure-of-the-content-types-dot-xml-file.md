---
title: 構造、Content_types] .xml ファイル |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d5892ab545c41f7d58f0d097f3d27c90c090f0ff
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736576"
---
# <a name="the-structure-of-the-contenttypesxml-file"></a>構造、Content_types] .xml ファイル
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSIX パッケージ内のコンテンツの種類についてを説明します。 Visual Studio は、パッケージをインストールする [Content_Types] .xml ファイルを使用しますが、ファイル自体はインストールされません。  
  
> [!NOTE]
>  [Content_Types] .xml ファイルの種類の一部は、このトピックでは VSIX パッケージで使用されている [Content_Type] .xml ファイルにのみ適用されますが、 *Open Packaging Conventions (OPC)* 標準。 詳細については、次を参照してください。 [OPC: A 新しい標準のパッケージ化、データ](http://go.microsoft.com/fwlink/?LinkID=148207)MSDN Web サイト。  
  
## <a name="attributes-and-elements"></a>属性および要素  
 次のセクションでは、ルート要素とその属性と子要素について説明します。  
  
### <a name="root-element"></a>ルート要素  
  
|要素|説明|  
|-------------|-----------------|  
|`Types`|VSIX パッケージ内のファイルの種類を列挙する子要素が含まれています。|  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`Xmlns`|(必須) この [Content_Types] .xml ファイルで使用されるスキーマの場所。|  
  
### <a name="attribute-name-attribute"></a>{Name} 属性属性  
  
|                           [値]                           |                説明                |
|-----------------------------------------------------------|-------------------------------------------|
| http://schemas.openformats.org/package/2006/content-types | コンテンツ タイプのスキーマの場所。 |
  
### <a name="child-elements"></a>子要素  
 `Types`要素は、任意の数を含めることができます`Default`要素。  
  
|要素|説明|  
|-------------|-----------------|  
|`Default`|VSIX パッケージ内のコンテンツの種類について説明します。 パッケージ内のすべてのファイル種類する必要がありますが、独自`Default`要素。|  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`Extension`|VSIX パッケージ内のファイルのファイル名拡張子。|  
|`ContentType`|ファイル名拡張子に関連付けられているコンテンツの種類について説明します。|  
  
### <a name="attribute-name-attribute"></a>{Name} 属性属性  
 Visual Studio は、次を認識`ContentType`関連付けられている値`Extension`型。  
  
|拡張子|ContentType|  
|---------------|-----------------|  
|txt|テキスト/プレーン|  
|pkgdef|テキスト/プレーン|  
|xml|text/xml|  
|vsixmanifest|text/xml|  
|htm ファイルや html|text/html|  
|rtf|アプリケーション/rtf|  
|pdf|アプリケーション/pdf|  
|gif|gif イメージ/|  
|jpg または jpeg|jpg イメージ/|  
|Tiff|tiff イメージ/|  
|vsix|アプリケーションまたは zip|  
|zip|アプリケーションまたは zip|  
|dll|application/octet-stream|  
|その他のすべてのファイルの種類|application/octet-stream|  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次の [Content_Types] .xml ファイルには、一般的な VSIX パッケージについて説明します。  
  
### <a name="code"></a>コード  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">  
    <Default Extension="vsixmanifest" ContentType="text/xml" />   
    <Default Extension="dll" ContentType="application/octet-stream" />   
    <Default Extension="png" ContentType="application/octet-stream" />   
    <Default Extension="txt" ContentType="text/plain" />   
    <Default Extension="pkgdef" ContentType="text/plain" />   
</Types>  
```  
  
## <a name="see-also"></a>関連項目  
 [VSIX パッケージの構造](../extensibility/anatomy-of-a-vsix-package.md)   
 [VSIX 拡張機能スキーマ 1.0 リファレンス](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC: データをパッケージ化するための新しい標準](http://go.microsoft.com/fwlink/?LinkID=148207)

