---
title: '&lt;値&gt;(JavaScript) |Microsoft Docs'
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
- <value> JavaScript XML tag
- value JavaScript XML tag
ms.assetid: 983e31de-cb1d-411e-b60d-eea6698a26f6
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bdb645bed570df019c4f4fe15b6865e1197bec67
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47546438"
---
# <a name="ltvaluegt-javascript"></a>&lt;値&gt;(JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Visual Studio 2017 ドキュメント](https://docs.microsoft.com/en-us/visualstudio/)します。  
  
ECMAScript 3 プロパティの `get` および `set` 関数のドキュメント情報を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
<value type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    locid="descriptionID">description  
</value>  
```  
  
#### <a name="parameters"></a>パラメーター  
 `type`  
 任意。 プロパティのデータ型です。 型は以下のいずれかです。  
  
-   `Number` や `Object` など、ECMAScript 5 仕様に含まれる ECMAScript 言語の型。  
  
-   `HTMLElement`、`Window`、`Document` などの DOM オブジェクト。  
  
-   JavaScript のコンストラクター関数。  
  
 `integer`  
 任意。 `type` が `Number` である場合に、プロパティが整数かどうかを指定します。 プロパティが整数であることを示す場合は `true` に設定します。それ以外の場合は `false` に設定します。 Visual Studio では、この属性は IntelliSense 情報を提供するためには使用されません。  
  
 `domElement`  
 任意。 この属性は非推奨とされました。この属性より `type` 属性が優先されます。 この属性は、ドキュメント化されたプロパティが DOM 要素であるかどうかを指定します。 プロパティが DOM 要素であることを指定する場合は `true` に設定します。それ以外の場合は `false` に設定します。 `type` 属性が設定されておらず `domElement` が `true` に設定されている場合、IntelliSense の入力候補機能では、ドキュメント化されたプロパティが `HTMLElement` として処理されます。  
  
 `mayBeNull`  
 任意。 ドキュメント化されたプロパティを null に設定できるかどうかを指定します。 プロパティを null に設定できることを示す場合は `true` に設定します。それ以外の場合は `false` に設定します。 既定値は `false` です。 Visual Studio では、この属性は IntelliSense 情報を提供するためには使用されません。  
  
 `elementType`  
 任意。 `type` が `Array` であれば、この属性は、配列内の要素の型を指定します。  
  
 `elementInteger`  
 任意。 `type` が `Array` であり、`elementType` が `Number` である場合、この属性は、配列内の要素が整数であるかどうかを指定します。 配列内の要素が整数であることを示す場合は `true` に設定します。それ以外の場合は `false` に設定します。 Visual Studio では、この属性は IntelliSense 情報を提供するためには使用されません。  
  
 `elementDomElement`  
 任意。 この属性は非推奨とされました。この属性より `elementType` 属性が優先されます。 `type` が `Array` である場合、この属性は、配列内の要素が DOM 要素であるかどうかを指定します。 要素が DOM 要素であることを指定する場合は `true` に設定します。それ以外の場合は `false` に設定します。 `elementType` 属性が設定されておらず `elementDomElement` が `true` に設定されている場合、IntelliSense の入力候補機能では、配列内の各要素が `HTMLElement` として処理されます。  
  
 `elementMayBeNull`  
 任意。 `type` が `Array` である場合、配列内の要素を null に設定できるかどうかを指定します。 配列内の要素を null に設定できることを示す場合は `true` に設定します。それ以外の場合は `false` に設定します。 既定値は `false` です。 Visual Studio では、この属性は IntelliSense 情報を提供するためには使用されません。  
  
 `locid`  
 任意。 プロパティに関するローカライズ情報用の識別子。 この識別子は、メンバーの ID であるか、または OpenAjax のメタデータで定義されているメッセージ バンドル内の `name` 属性値に対応します。 識別子の型で指定された形式によって異なります、 [ \<loc >](../ide/loc-javascript.md)要素。  
  
 `description`  
 任意。 プロパティの説明  
  
## <a name="remarks"></a>Remarks  
 ECMAScript 5 プロパティの使用、 [\<概要 >](../ide/summary-javascript.md)要素。  
  
 `<value>` または `get` 関数の直前の `set` 要素を使用します。  
  
## <a name="example"></a>例  
 次のコード例に、`<value>` 関数で `get` 要素を使用する方法を示します。  
  
```javascript  
function Sys$CancelEventArgs$get_cancel() {  
    /// <value type="Boolean" locid="P:J#Sys.CancelEventArgs.cancel"></value>  
    if (arguments.length !== 0) throw Error.parameterCount();  
    return this._cancel();  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [XML ドキュメント コメント](../ide/xml-documentation-comments-javascript.md)



