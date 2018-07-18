---
title: ビットマップ要素 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2456e68088208e4915fe4809c411e5ec002de7b8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31098109"
---
# <a name="bitmap-element"></a>ビットマップ要素
ビットマップを定義します。 ビットマップには、リソース、またはファイルが読み込まれます。  
  
## <a name="syntax"></a>構文  
  
```  
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|guid|必須。 GUID と ID コマンド id の GUID です。<br /><br /> ビットマップの guid 属性は、VSPackage またはその他のコマンドのグループに関連付けではありません。  ビットマップの定義に一意である必要があり、その他の目的は使用できません。|  
|ResID|GUID と ID のコマンド識別子の ID です。 ResID または href 属性のいずれかが必要です。<br /><br /> ResID 属性は、コマンド テーブルのマージ中に読み込まれるには、ビットマップ ストリップを決定する整数リソース ID です。  コマンド テーブルが読み込まれるときに、リソース ID で指定したビットマップが、同じモジュールのリソースから読み込まれます。|  
|usedList|ResID 属性があるかどうかに必要です。 ビットマップ ストリップの利用可能なイメージを選択します。|  
|href|ビットマップへのパス。 ResID または href 属性のいずれかが必要です。<br /><br /> 結果のバイナリに組み込まれている指定されたイメージ ファイルのインクルード パスが検索されます。  コマンド テーブルのマージ中に、イメージがコピーされ、その他のリソースの検索または読み込みは必要ありません。  UsedList 属性が存在しない場合はストリップ内のすべてのイメージのとおりです。 **注:** .bmp や .gif、.png、いくつかの形式のいずれかでイメージを指定することがあります。  以前のバージョンのコンパイラは、アルファ情報部分の透過性のある 32 ビットのビットマップ イメージをサポートしていません。 これらのバージョンの回避策では、.png 形式を使用します。|  
|条件|任意。 参照してください[条件付き属性](../extensibility/vsct-xml-schema-conditional-attributes.md)です。|  
  
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