---
title: '&lt;var&gt; (JavaScript) |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <var> JavaScript XML tag
- var JavaScript XML tag
ms.assetid: 34ff9023-c81c-46d1-85b6-0022f0962e66
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 98bf86f807874fefe066ed2d1008e31451fbbba0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54802662"
---
# <a name="ltvargt-javascript"></a>&lt;var&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

変数のドキュメント情報を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
<var type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    helpKeyword="keyword" locid="descriptionID">description  
</var>   
```  
  
#### <a name="parameters"></a>パラメーター  
 `type`  
 任意。 変数のデータ型。 型は以下のいずれかです。  
  
- `Number` や `Object` など、ECMAScript 5 仕様に含まれる ECMAScript 言語の型。  
  
- `HTMLElement`、`Window`、`Document` などの DOM オブジェクト。  
  
- JavaScript のコンストラクター関数。  
  
  `integer`  
  任意。 `type` が `Number` である場合に、変数が整数かどうかを指定します。 変数が整数であることを示す場合は `true` に設定します。それ以外の場合は `false` に設定します。 Visual Studio では、この属性は IntelliSense 情報を提供するためには使用されません。  
  
  `domElement`  
  任意。 この属性は非推奨とされました。この属性より `type` 属性が優先されます。 この属性は、ドキュメント化された変数が DOM 要素であるかどうかを指定します。 変数が DOM 要素であることを指定する場合は `true` に設定します。それ以外の場合は `false` に設定します。 `type` 属性が設定されておらず `domElement` が `true` に設定されている場合、IntelliSense の入力候補機能では、ドキュメント化された変数が `HTMLElement` として処理されます。  
  
  `mayBeNull`  
  任意。 ドキュメント化された変数を null に設定できるかどうかを指定します。 変数を null に設定できることを示す場合は `true` に設定します。それ以外の場合は `false` に設定します。 既定値は `false` です。 Visual Studio では、この属性は IntelliSense 情報を提供するためには使用されません。  
  
  `elementType`  
  任意。 `type` が `Array` であれば、この属性は、配列内の要素の型を指定します。  
  
  `elementInteger`  
  任意。 `type` が `Array` であり、`elementType` が `Number` である場合、この属性は、配列内の要素が整数であるかどうかを指定します。 配列内の要素が整数であることを示す場合は `true` に設定します。それ以外の場合は `false` に設定します。 Visual Studio では、この属性は IntelliSense 情報を提供するためには使用されません。  
  
  `elementDomElement`  
  任意。 この属性は非推奨とされました。この属性より `elementType` 属性が優先されます。 `type` が `Array` である場合、この属性は、配列内の要素が DOM 要素であるかどうかを指定します。 要素が DOM 要素であることを指定する場合は `true` に設定します。それ以外の場合は `false` に設定します。 `elementType` 属性が設定されておらず `elementDomElement` が `true` に設定されている場合、IntelliSense の入力候補機能では、配列内の各要素が `HTMLElement` として処理されます。  
  
  `elementMayBeNull`  
  任意。 `type` が `Array` である場合、配列内の要素を null に設定できるかどうかを指定します。 配列内の要素を null に設定できることを示す場合は `true` に設定します。それ以外の場合は `false` に設定します。 既定値は `false` です。 Visual Studio では、この属性は IntelliSense 情報を提供するためには使用されません。  
  
  `helpKeyword`  
  任意。 F1 ヘルプのキーワード。  
  
  `locid`  
  任意。 変数に関するローカライズ情報用の識別子。 この識別子は、メンバーの ID であるか、または OpenAjax のメタデータで定義されているメッセージ バンドル内の `name` 属性値に対応します。 識別子の型で指定された形式によって異なります、 [ \<loc >](../ide/loc-javascript.md)タグ。  
  
  `description`  
  任意。 変数の説明。  
  
## <a name="example"></a>例  
 `<var>` 要素を使用する方法を次のコード例に示します。  
  
```javascript  
/// <var>A rectangle that has a width of 5.</var>  
var Rectangle = {  
    /// <field type = 'Number'>The width of the rectangle.</field>  
    wid: 5,  
    /// <field type = 'Number'>The length of the rectangle.</field>  
    len: 0,  
    /// <field type='Number'>Returns the area of the rectangle.</field>  
    getArea: function (wid, len) {  
        return len * wid;  
    }  
}  
```  
  
## <a name="see-also"></a>「  
 [XML ドキュメント コメント](../ide/xml-documentation-comments-javascript.md)
