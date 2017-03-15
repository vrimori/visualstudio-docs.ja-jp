---
title: "[Content_types] .xml ファイルの構造 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 7278fb37984b92a6a07823c552db5c59a446d0d2
ms.openlocfilehash: 6f45707a88a27fa54840825d9562f859385ce4b7
ms.lasthandoff: 02/22/2017

---
# <a name="the-structure-of-the-contenttypesxml-file"></a>[Content_types] .xml ファイルの構造
VSIX パッケージ内のコンテンツの種類についてを説明します。 Visual Studio は [Content_Types] .xml ファイルを使用して、パッケージのインストールが、ファイル自体はインストールされません。  
  
> [!NOTE]
>  [Content_Types] .xml ファイルの種類の一部は、このトピックの VSIX パッケージで使用されている [Content_Type] .xml ファイルにのみ適用されますが、 *Open Packaging Conventions (OPC)*標準です。 詳細については、次を参照してください。 [OPC: A 新しい標準のパッケージ化、データ](http://go.microsoft.com/fwlink/?LinkID=148207)MSDN Web サイトです。  
  
## <a name="attributes-and-elements"></a>属性および要素  
 次のセクションでは、ルート要素とその属性と子要素について説明します。  
  
### <a name="root-element"></a>ルート要素  
  
|要素|説明|  
|-------------|-----------------|  
|`Types`|VSIX パッケージ内のファイルの種類を列挙する子要素が含まれています。|  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`Xmlns`|(必須) この [Content_Types] .xml ファイルを使用するスキーマの場所。|  
  
### <a name="attribute-name-attribute"></a>{属性 name}属性  
  
|値|説明|  
|-----------|-----------------|  
|http://schemas.openformats.org/package/2006/content-types|コンテンツの種類のスキーマの場所。|  
  
### <a name="child-elements"></a>子要素  
 `Types`要素は、任意の数を含めることができます`Default`要素。  
  
|要素|説明|  
|-------------|-----------------|  
|`Default`|VSIX パッケージ内のコンテンツの種類について説明します。 パッケージのすべてのファイル タイプがあります独自`Default`要素。|  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`Extension`|VSIX パッケージ内のファイルのファイル名拡張子。|  
|`ContentType`|ファイル名拡張子に関連付けられているコンテンツの種類について説明します。|  
  
### <a name="attribute-name-attribute"></a>{属性 name}属性  
 Visual Studio は、次を認識`ContentType`関連付けられた値`Extension`型です。  
  
|拡張子|ContentType|  
|---------------|-----------------|  
|txt|テキスト/プレーン|  
|pkgdef|テキスト/プレーン|  
|xml|text/xml|  
|vsixmanifest|text/xml|  
|htm ファイルや html|テキストと html|  
|rtf|アプリケーション/rtf|  
|pdf|アプリケーション/pdf|  
|gif|gif イメージ/|  
|jpg または jpeg|jpg イメージ/|  
|tiff|tiff イメージ/|  
|vsix|アプリケーション/zip|  
|zip|アプリケーション/zip|  
|dll|アプリケーションまたはオクテット ストリーム|  
|その他のすべてのファイルの種類|アプリケーションまたはオクテット ストリーム|  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次の [Content_Types] .xml ファイルでは、一般的な VSIX パッケージについて説明します。  
  
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
 [OPC: データのパッケージ化するための新しい標準](http://go.microsoft.com/fwlink/?LinkID=148207)
