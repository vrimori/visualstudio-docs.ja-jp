---
title: "オブジェクトはオブジェクト (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: object
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Object object
ms.assetid: d24ef8fc-217b-4828-94e1-19f72780bae0
caps.latest.revision: "25"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17e82b9c66c286c7f847e7b67b1b5928aadd613e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="object-object-javascript"></a>Object オブジェクト (JavaScript)
すべての [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] オブジェクトに共通する機能を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
  
obj  
 = new Object([value])   
```  
  
## <a name="parameters"></a>パラメーター  
 `obj`  
 必須です。 `Object` オブジェクトを代入する変数名を指定します。  
  
 *value*  
 省略可能です。 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] の任意のプリミティブ データ型 (Number、Boolean、または String) を指定します。 オブジェクトの場合、そのオブジェクは変更されずに返されます。 場合*値*は`null`、**未定義**、または省略すると、コンテンツを持つオブジェクトが作成されます。  
  
## <a name="remarks"></a>コメント  
 `Object` オブジェクトは、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] の他のすべてのオブジェクトに含まれます。このオブジェクトのすべてのメソッドとプロパティは、他のすべてのオブジェクトで使用できます。 メソッドは、ユーザー定義オブジェクト内で再定義でき、必要なときに [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] から呼び出されます。 **ToString**メソッドは頻繁に再定義の例`Object`メソッドです。  
  
 この言語リファレンスにおける `Object` の各メソッドの説明には、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] の組み込みオブジェクトの既定の実装およびオブジェクト固有の実装の両方の情報が含まれます。  
  
## <a name="requirements"></a>要件  
 `Object Object` は、[!INCLUDE[jsv3text](../../javascript/reference/includes/jsv3text-md.md)] で導入されました。 次の一覧にあるメンバーの一部は、それ以降のバージョンで導入されています。  
  
## <a name="properties"></a>プロパティ  
 `Object Object` のプロパティを次の表に示します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|[__proto\_ \_プロパティ](../../javascript/reference/proto-property-object-javascript.md)|オブジェクトのプロトタイプを指定します。|  
|[constructor プロパティ](../../javascript/reference/constructor-property-object-javascript.md)|オブジェクトを作成する関数を指定します。|  
|[prototype プロパティ](../../javascript/reference/prototype-property-object-javascript.md)|指定されたオブジェクトのクラスのプロトタイプへの参照を返します。|  
  
## <a name="functions"></a>関数  
 `Object Object` の関数を次の表に示します。  
  
|関数|説明|  
|--------------|-----------------|  
|[Object.assign 関数](../../javascript/reference/object-assign-function-object-javascript.md)|1 つ以上のソース オブジェクトからターゲット オブジェクトに値をコピーします。|  
|[Object.create 関数](../../javascript/reference/object-create-function-javascript.md)|指定されたプロトタイプを持ち、指定されたプロパティを含む (オプション) オブジェクトを作成します。|  
|[Object.defineProperties 関数](../../javascript/reference/object-defineproperties-function-javascript.md)|1 つ以上のプロパティをオブジェクトに追加したり既存のプロパティの属性を変更したります。|  
|[Object.defineProperty 関数](../../javascript/reference/object-defineproperty-function-javascript.md)|1 つのプロパティをオブジェクトに追加したり既存のプロパティの属性を変更したります。|  
|[Object.freeze 関数](../../javascript/reference/object-freeze-function-javascript.md)|既存のプロパティ属性と値の変更、および新しいプロパティの追加を防止します。|  
|[Object.getOwnPropertyDescriptor 関数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)|データ プロパティまたはアクセサー プロパティの定義を返します。|  
|[Object.getOwnPropertyNames 関数](../../javascript/reference/object-getownpropertynames-function-javascript.md)|オブジェクトのプロパティおよびメソッドの名前を返します。|  
|[Object.getOwnPropertySymbols 関数](../../javascript/reference/object-getownpropertysymbols-function-javascript.md)|オブジェクトのシンボル プロパティを返します。|  
|[Object.getPrototypeOf 関数](../../javascript/reference/object-getprototypeof-function-javascript.md)|オブジェクトのプロトタイプを返します。|  
|[Object.is 関数](../../javascript/reference/object-is-function-javascript.md)|2 つの値が同じ値であるかどうかを示す値を返します。|  
|[Object.isExtensible 関数](../../javascript/reference/object-isextensible-function-javascript.md)|新しいプロパティをオブジェクトに追加できるかどうかを示す値を返します。|  
|[Object.isFrozen 関数](../../javascript/reference/object-isfrozen-function-javascript.md)|オブジェクトの既存のプロパティ属性と値を変更できず、オブジェクトに新しいプロパティも追加できない場合は、`true` を返します。|  
|[Object.isSealed 関数](../../javascript/reference/object-issealed-function-javascript.md)|オブジェクトの既存のプロパティ属性および値を変更できず、オブジェクトへの新しいプロパティの追加もできない場合は、`true` を返します。|  
|[Object.keys 関数](../../javascript/reference/object-keys-function-javascript.md)|オブジェクトの列挙可能なプロパティおよびメソッドの名前を返します。|  
|[Object.preventExtensions 関数](../../javascript/reference/object-preventextensions-function-javascript.md)|オブジェクトへの新しいプロパティの追加を防止します。|  
|[Object.seal 関数](../../javascript/reference/object-seal-function-javascript.md)|既存のプロパティの属性の変更、および新しいプロパティの追加を防止します。|  
|[Object.setPrototypeOf 関数](../../javascript/reference/object-setprototypeof-function-javascript.md)|オブジェクトのプロトタイプを設定します。|  
  
## <a name="methods"></a>メソッド  
 `Object Object` のメソッドを次の表に示します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[hasOwnProperty メソッド](../../javascript/reference/hasownproperty-method-object-javascript.md)|指定した名前のプロパティがオブジェクトにあるかどうかを表すブール値を返します。|  
|[isPrototypeOf メソッド](../../javascript/reference/isprototypeof-method-object-javascript.md)|オブジェクトが、別のオブジェクトのプロトタイプ階層に存在するかどうかを表すブール値を返します。|  
|[propertyIsEnumerable メソッド](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|指定したプロパティがオブジェクトの一部であるかどうか、および列挙可能かどうかを表すブール値を返します。|  
|[toLocaleString メソッド](../../javascript/reference/tolocalestring-method-object-javascript.md)|現在のロケールに基づいて、オブジェクトを文字列に変換して返します。|  
|[toString メソッド](../../javascript/reference/tostring-method-object-javascript.md)|オブジェクトの値を表す文字列を返します。|  
|[valueOf メソッド](../../javascript/reference/valueof-method-object-javascript.md)|指定されたオブジェクトのプリミティブ値を返します。|  
  
## <a name="see-also"></a>関連項目  
 [JavaScript オブジェクト](../../javascript/reference/javascript-objects.md)