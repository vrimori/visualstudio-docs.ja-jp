---
title: データ プロパティとアクセサー プロパティ | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 7e132831-375d-4728-9a57-5c6f91075b1c
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b800131ba76aa432492c0caefdbb9e8d5291924
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569472"
---
# <a name="data-properties-and-accessor-properties"></a>データ プロパティとアクセサー プロパティ
このセクションには、データ プロパティとアクセサー プロパティについて必要になる可能性のある情報がすべて含まれています。  
  
### <a name="data-properties"></a>データ プロパティ  
 *データ プロパティ*は、値を取得および設定できるプロパティです。 データ プロパティの記述子には `value` および `writable` のプロパティが含まれています。  
  
 次の表は、データ プロパティの記述子の属性を一覧表示したものです。  
  
|データ記述子の属性|説明|既定値|  
|-------------------------------|-----------------|-------------|  
|`value`|プロパティの現在値。|`undefined`|  
|`writable`|`true` または `false`。 `writable` が `true` に設定されている場合、プロパティ値を変更することができます。|`false`|  
|`enumerable`|`true` または `false`。 `enumerable` が `true` に設定されている場合、プロパティを `for...in` ステートメントで列挙することができます。|`false`|  
|`configurable`|`true` または `false`。 `configurable` が `true` に設定されている場合、プロパティの属性を変更でき、プロパティを削除することができます。|`false`|  
  
 記述子に `value`、`writable`、`get`、または `set` の属性が含まれておらず、指定したプロパティ名が存在しない場合、データ プロパティが追加されます。  
  
 `configurable` 属性が `false` で、`writable` が `true` である場合、`value` および `writable` 属性を変更することができます。  
  
#### <a name="data-properties-added-without-using-defineproperty"></a>defineProperty を使用せずに追加されたデータ プロパティ  
 `Object.defineProperty`、`Object.defineProperties`、または `Object.create` 関数を使用せずにデータ プロパティを追加すると、`writable`、`enumerable`、および `configurable` 属性がすべて `true` に設定されます。 プロパティが追加されると、`Object.defineProperty` 関数を使用することで変更ができるようになります。  
  
 次の方法を使用して、データ プロパティを追加できます。  
  
-   代入演算子 (=) (例: `obj.color = "white";`)  
  
-   オブジェクト リテラル (例: `obj = { color: "white", height: 5 };`)  
  
-   コンストラクション関数 (「[Using Constructors to Define Types](../../javascript/advanced/using-constructors-to-define-types.md)」(コンストラクターを使用した型の定義) を参照)  
  
### <a name="accessor-properties"></a>アクセサー プロパティ  
 *アクセサー プロパティ*は、プロパティ値が設定または取得されるたびにユーザーが指定した関数を呼び出します。 アクセサー プロパティの記述子には、`get` 属性、`set` 属性、またはその両方が含まれます。  
  
 次の表は、アクセサー プロパティの記述子の属性を一覧表示したものです。  
  
|アクセサー記述子の属性|説明|既定値|  
|-----------------------------------|-----------------|-------------|  
|`get`|プロパティ値を戻す関数。 この関数にはパラメーターがありません。|`undefined`|  
|`set`|プロパティ値を設定する関数。 割り当てられる値を含むパラメーターが 1 つあります。|`undefined`|  
|`enumerable`|`true` または `false`。 `enumerable` が `true` に設定されている場合、プロパティを `for...in` ステートメントで列挙することができます。|`false`|  
|`configurable`|`true` または `false`。 `configurable` が `true` に設定されている場合、プロパティの属性を変更でき、プロパティを削除することができます。|`false`|  
  
 `get` アクセサーが未定義である場合にプロパティ値へのアクセスが試行されると、値 `undefined` が戻されます。 `set` アクセサーが未定義である場合にアクセサー プロパティへの値の割り当てが試行された場合は、何も起こりません。  
  
### <a name="property-modifications"></a>プロパティの変更  
 オブジェクトに指定した名前のプロパティが既に含まれている場合は、プロパティの属性が変更されます。 プロパティを変更しても、記述子で指定されていない属性は変わりません。  
  
 既存のプロパティの `configurable` 属性が `false` の場合、許可されている変更は、`true` から `false` への `writable` 属性の変更のみです。  
  
 データ プロパティからアクセサー プロパティに、およびその逆の変更ができます。 変更を行っても、記述子で指定されていない `configurable` および `enumerable` 属性はプロパティに保持されます。 記述子で指定されていないその他の属性は、既定値に設定されます。  
  
 `Object.defineProperty` 関数に複数の呼び出しを行うことで、構成可能なアクセサー プロパティを段階的に定義できます。 たとえば、`Object.defineProperty` の 1 回の呼び出しでは、`get` アクセサーのみが定義されます。 同じプロパティ名に対して再度呼び出しを行うと、`set` アクセサーを定義することができます。 これで、このプロパティに `get` アクセサーと `set` アクセサーの両方が含まれます。  
  
 既存のプロパティに適用される記述子オブジェクトを取得するには、[Object.getOwnPropertyDescriptor 関数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md) を使用します。  
  
 [Object.seal 関数](../../javascript/reference/object-seal-function-javascript.md)と [Object.freeze 関数](../../javascript/reference/object-freeze-function-javascript.md)を使用して、プロパティ属性の変更を防ぐことができます。