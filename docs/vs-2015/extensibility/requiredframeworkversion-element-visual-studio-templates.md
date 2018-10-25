---
title: RequiredFrameworkVersion 要素 (Visual Studio テンプレート) |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 374ee45be29dd51a2a29d1c949939d1d3b939aa3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49171797"
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>RequiredFrameworkVersion 要素 (Visual Studio テンプレート)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

テンプレートで必要とされる最小の .NET Framework バージョンを指定します。スキーマの階層。  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<RequiredFrameworkVersion >  
  
## <a name="syntax"></a>構文  
  
```  
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
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
  
 テキストは、テンプレートに必要な .NET Framework の最小バージョン番号である必要があります。  
  
## <a name="remarks"></a>Remarks  
 `RequiredFrameworkVersion` は、省略可能な要素です。 テンプレートは、特定の最小バージョンと .NET Framework の存在する場合、以降のバージョンのみがサポートする場合は、この要素を使用します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)   
 [対象となる特定の .NET Framework バージョンの指定](../ide/targeting-a-specific-dotnet-framework-version.md)

