---
title: '&lt;概要&gt;(JavaScript) |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- summary JavaScript XML tag
- <summary> JavaScript XML tag
ms.assetid: 6540582d-bdb3-42ec-ad2f-c176783e6f9c
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 79aeb36e62279dcdafd2adb0143fa70ce2ee0eba
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47544930"
---
# <a name="ltsummarygt-javascript"></a>&lt;概要&gt;(JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Visual Studio 2017 ドキュメント](https://docs.microsoft.com/en-us/visualstudio/)します。  
  
関数またはメソッドの説明を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
<summary locid="descriptionID">description  
</summary>  
```  
  
#### <a name="parameters"></a>パラメーター  
 `locid`  
 任意。 関数またはメソッドに関するローカライズ情報用の識別子。 この識別子は、メンバーの ID であるか、または OpenAjax のメタデータで定義されているメッセージ バンドル内の `name` 属性値に対応します。 識別子の型で指定された形式によって異なります、 [ \<loc >](../ide/loc-javascript.md)要素。  
  
 `description`  
 任意。 関数またはメソッドの説明。  
  
## <a name="remarks"></a>Remarks  
 含める関数の注釈に使用する要素[\<概要 >](../ide/summary-javascript.md)、 [ \<param >](../ide/param-javascript.md)、および[\<返します >](../ide/returns-javascript.md)、ステートメントの前に、の関数本体に配置する必要があります。  
  
## <a name="example"></a>例  
 次のコードに、`<summary>` 要素を使用する方法を示します。  
  
```javascript  
function areaFunction(radiusParam)  
{  
    /// <summary>Determines the area of a circle when supplied a radius parameter.</summary>  
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>  
    /// <returns type="Number">The area.</returns>  
    var areaVal;  
    areaVal = Math.PI * radiusParam * radiusParam;  
    return areaVal;  
}  
  
```  
  
## <a name="see-also"></a>関連項目  
 [XML ドキュメント コメント](../ide/xml-documentation-comments-javascript.md)



