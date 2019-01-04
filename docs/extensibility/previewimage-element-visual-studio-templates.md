---
title: PreviewImage 要素 (Visual Studio テンプレート) |Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <PreviewImage> Element (Visual Studio Templates)
- PreviewImage Element (Visual Studio Templates)
ms.assetid: d1796f20-523b-4e0d-8ac3-ca87f3b5a9b6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b0e2c2f5f4914fafbf37daa5fbc8a9218c8e0482
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53913398"
---
# <a name="previewimage-element-visual-studio-templates"></a>PreviewImage 要素 (Visual Studio テンプレート)
いずれかで表示されるプレビュー イメージのファイル名として、プレビュー イメージを指定します、**新しいプロジェクト**または**新しい項目の追加** ダイアログ ボックス。  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<PreviewImage >  
  
## <a name="syntax"></a>構文  
  
```  
<PreviewImage>"filename"</PreviewImage>  
```  
  
## <a name="attributes-and-elements"></a>属性と要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必須の要素です。<br /><br /> テンプレートを分類し、いずれかでの表示方法を定義、**新しいプロジェクト**または**新しい項目の追加** ダイアログ ボックス。|  
  
## <a name="text-value"></a>テキスト値  
 テキスト値が必要です。  
  
 テキストは、ファイル名を表す文字列である必要があります。  
  
## <a name="remarks"></a>Remarks  
 `PreviewImage` は、省略可能な要素です。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)