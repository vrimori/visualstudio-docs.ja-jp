---
title: '&lt;非推奨とされます&gt;(JavaScript) |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: cf33d371-59da-4310-95ee-d7524fd9d58c
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b93a2b4dcc541f32c16766da0dd9dd19a4fdfe0d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54759757"
---
# <a name="ltdeprecatedgt-javascript"></a>&lt;非推奨とされます&gt;(JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

非推奨の関数またはメソッドを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
<deprecated  
    type="deprecate|remove"  
    locid="descriptionID">description  
</deprecated>  
```  
  
#### <a name="parameters"></a>パラメーター  
 `type`  
 任意。 関数またはメソッドが将来のリリースで削除されるかどうか、または関数またはメソッドが既に削除されていて、使用するとエラーが発生することがあるかどうかを指定します。 関数またはメソッドが将来のリリースで削除されることを指定するには、`deprecate` に設定します。 関数またはメソッドが既に削除されたことを指定するには、`remove` に設定します。  
  
 `locid`  
 任意。 関数またはメソッドに関するローカライズ情報用の識別子。 この識別子は、メンバーの ID であるか、または OpenAjax のメタデータで定義されているメッセージ バンドル内の `name` 属性値に対応します。 識別子の型で指定された形式によって異なります、 [ \<loc >](../ide/loc-javascript.md)要素。  
  
 `description`  
 任意。 非推奨となる関数またはメソッドの説明。  
  
## <a name="remarks"></a>コメント  
 `<deprecated>` など、関数の注釈に使用される要素は、ステートメントの前の関数本体に配置する必要があります。 交換することをお勧め関数を非推奨としてマークすると、その[\<概要 >](../ide/summary-javascript.md)を持つ要素、`<deprecated>`要素。  
  
## <a name="example"></a>例  
 次のコードに、`<deprecated>` 要素を使用する方法を示します。  
  
```javascript  
function areaFunction(radiusParam) {  
    /// <deprecated type="deprecate" >Determines the area of a circle when supplied a radius parameter.</deprecated>  
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>  
    /// <returns type="Number">The area.</returns>  
    var areaVal;  
    areaVal = Math.PI * radiusParam * radiusParam;  
    return areaVal;  
}  
  
```  
  
## <a name="see-also"></a>「  
 [XML ドキュメント コメント](../ide/xml-documentation-comments-javascript.md)
