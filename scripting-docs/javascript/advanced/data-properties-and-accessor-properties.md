---
title: "データ プロパティとアクセサー プロパティ | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 7e132831-375d-4728-9a57-5c6f91075b1c
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# データ プロパティとアクセサー プロパティ
このセクションでは、データ プロパティおよびアクセサー プロパティに関して必要になるすべての情報について説明します。  
  
### データ プロパティ  
 *データ プロパティ*は、値を取得および設定できるプロパティです。  データ プロパティの記述子には、`value` プロパティと `writable` プロパティがあります。  
  
 データ プロパティの記述子の属性を次の表に示します。  
  
|データ記述子の属性|説明|既定値|  
|---------------|--------|---------|  
|`value`|プロパティの現在値。|`undefined`|  
|`writable`|`true` または `false`。  `writable` が `true` に設定されていると、プロパティ値を変更できます。|`false`|  
|`enumerable`|`true` または `false`。  `enumerable` が `true`に設定されていると、プロパティは `for…in` ステートメントによって列挙できます。|`false`|  
|`configurable`|`true` または `false`。  `configurable` が `true`に設定されていると、プロパティ属性の変更およびプロパティの削除ができます。|`false`|  
  
 記述子に `value` 属性、`writable` 属性、`get` 属性、または `set` 属性がなく、指定されたプロパティ名が見つからない場合は、データ プロパティが追加されます。  
  
 `configurable` 属性が `false`、 `writable` 属性が `true` の場合、 `value` 属性と `writable` 属性を変更できます。  
  
#### defineProperty を使用せずに追加されたデータ プロパティ  
 `Object.defineProperty` 関数、`Object.defineProperties` 関数、または `Object.create` 関数を使用せずにデータ プロパティを追加する場合、`writable` 属性、`enumerable` 属性、および `configurable` 属性はすべて `true` に設定されます。  追加したプロパティは、`Object.defineProperty` 関数を使用して変更できます。  
  
 データ プロパティを追加するには、次の方法を使用できます。  
  
-   `obj.color = "white";` における代入演算子 \(\=\)  
  
-   `obj = { color: "white", height: 5 };` におけるオブジェクト リテラル  
  
-   「[コンストラクターを使用した型の定義](../../javascript/advanced/using-constructors-to-define-types.md)」で説明されているコンストラクター関数  
  
### アクセサー プロパティ  
 *アクセサー プロパティ*は、プロパティ値が設定または取得されるたびにユーザーが指定した関数を呼び出します。  アクセサー プロパティの記述子には、`get` 属性、`set` 属性、またはその両方が含まれます。  
  
 アクセサー プロパティの記述子の属性を次の表に示します。  
  
|アクセサー記述子の属性|説明|既定値|  
|-----------------|--------|---------|  
|`get`|プロパティ値を返す関数。  この関数にパラメーターはありません。|`undefined`|  
|`set`|プロパティ値を設定する関数。  割り当てる値を含むパラメーターが 1 つあります。|`undefined`|  
|`enumerable`|`true` または `false`。  `enumerable` が `true`に設定されていると、プロパティは `for…in` ステートメントによって列挙できます。|`false`|  
|`configurable`|`true` または `false`。  `configurable` が `true`に設定されていると、プロパティ属性の変更およびプロパティの削除ができます。|`false`|  
  
 `get` アクセサーが未定義でプロパティ値にアクセスしようとすると、`undefined` 値が返されます。  `set` アクセサーが未定義でアクセサー プロパティに値を代入しようとしても、何も実行されません。  
  
### プロパティの変更  
 オブジェクトに既に指定された名前のプロパティがある場合は、プロパティの属性が変更されます。  プロパティを変更する際に、記述子で指定されていない属性は変更されません。  
  
 既存のプロパティの `configurable` 属性が `false` の場合、許容される唯一の変更は `writable` 属性を `true` から `false` に変更することです。  
  
 データ プロパティはアクセサー プロパティに変更でき、その逆も可能です。  その場合、記述子に指定されていないプロパティ内の `configurable` 属性と `enumerable` 属性は維持されます。  記述子に指定されていない他の属性は、既定値に設定されます。  
  
 `Object.defineProperty` 関数を複数回呼び出すことにより、設定可能なアクセサー プロパティをインクリメント方式で定義できます。  たとえば、`Object.defineProperty` を 1 回呼び出して、`get` アクセサーのみを定義する場合があります。  同じプロパティ名をその後に呼び出して、`set` アクセサーを定義する場合があります。  そのプロパティには、`get` アクセサーと `set` アクセサーの両方が定義されます。  
  
 既存のプロパティに適用する記述子オブジェクトを取得するには、[Object.getOwnPropertyDescriptor 関数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md) を使用できます。  
  
 [Object.seal 関数](../../javascript/reference/object-seal-function-javascript.md) と [Object.freeze 関数](../../javascript/reference/object-freeze-function-javascript.md) を使用すると、プロパティの属性の変更を防止できます。