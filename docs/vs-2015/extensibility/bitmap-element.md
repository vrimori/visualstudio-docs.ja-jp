---
title: Bitmap 要素 |Microsoft Docs
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
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cbeb175c8e4f9902fafbfdb8df4f5d83387980a4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789942"
---
# <a name="bitmap-element"></a>Bitmap 要素
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ビットマップを定義します。 ビットマップには、リソースまたはファイルが読み込まれます。  
  
## <a name="syntax"></a>構文  
  
```  
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|guid|必須。 コマンド id を GUID と ID の GUID です。<br /><br /> ビットマップの guid 属性は、すべての VSPackage またはその他のコマンド グループに関連付けではありません。  ビットマップ定義に一意である必要があり、他の目的は使用しない必要があります。|  
|resID|コマンド id を GUID と ID の ID。 ResID または href 属性のいずれかが必要です。<br /><br /> ResID 属性は、コマンド テーブルのマージ中に読み込まれるされるビットマップ ストリップを決定する整数のリソース ID です。  コマンド テーブルが読み込まれるときに、リソース ID で指定されたビットマップは、同じモジュールのリソースから読み込まれます。|  
|usedList|ResID 属性が存在するかどうかに必要です。 ビットマップ ストリップで利用可能なイメージを選択します。|  
|href|ビットマップへのパス。 ResID または href 属性のいずれかが必要です。<br /><br /> 結果のバイナリに組み込まれている指定されたイメージ ファイルのインクルード パスが検索されます。  コマンド テーブルの結合時に、イメージがコピーされ、その他のリソースの検索や負荷は必要ありません。  UsedList 属性が存在しない場合は、ストリップ内のすべてのイメージを使用できます。 **注:** .bmp、.gif、.png を含むいくつかの形式のいずれかでイメージを指定することがあります。  以前のバージョンのコンパイラは、部分的に透明にアルファ情報が 32 ビットのビットマップ イメージをサポートしていません。 回避策これらのバージョンは .png 形式を使用することです。|  
|条件|任意。 参照してください[条件付き属性](../extensibility/vsct-xml-schema-conditional-attributes.md)します。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[Bitmaps 要素](../extensibility/bitmaps-element.md)|ビットマップの要素をグループ化します。|  
  
## <a name="example"></a>例  
  
```  
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />  
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"  
  usedList="1, 2, 3, 4"/>  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio Command Table (.Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

