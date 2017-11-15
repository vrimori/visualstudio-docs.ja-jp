---
title: "プロトタイプおよびプロトタイプの継承 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- prototype [JavaScript]
- prototype inheritance [JavaScript]
ms.assetid: 1e1d0631-2a9f-4011-b9fe-fa338e1ef34c
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ade60bcbbfad166bae18b650daa6906f9983d4cd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="prototypes-and-prototype-inheritance"></a>プロトタイプおよびプロトタイプの継承
JavaScript では、`prototype` は関数のプロパティ、およびコンストラクター関数によって作成されるオブジェクトのプロパティです。 関数のプロトタイプはオブジェクトです。 主に、関数がコンストラクターとして使用される場合に使用されます。  
  
```JavaScript  
function Vehicle(wheels, engine) {  
    this.wheels = wheels;  
    this.engine = engine;  
}  
```  
  
 前の例では、`Vehicle` 関数のプロトタイプは、`Vehicle` コンストラクターでインスタンス化されたオブジェクトのプロトタイプです。  
  
## <a name="using-prototypes-to-add-properties-and-methods"></a>プロトタイプを使用したプロパティとメソッドの追加  
 `prototype` プロパティを使用すると、オブジェクト (既に作成されているものも含む) にプロパティおよびメソッドを追加できます。  
  
```JavaScript  
var testVehicle = new Vehicle(2, false);  
Vehicle.prototype.color = "red";  
var testColor = testVehicle.color;  
```  
  
 `testColor` の値は "red" です。  
  
 定義済みオブジェクトにもプロパティおよびメソッドを追加できます。 たとえば、`Trim` プロトタイプ オブジェクトの `String` メソッドを定義できます。スクリプトのすべての文字列でメソッドが継承されます。  
  
```JavaScript  
String.prototype.trim = function()  
{  
    // Replace leading and trailing spaces with the empty string  
    return this.replace(/(^\s*)|(\s*$)/g, "");  
}  
var s = "    leading and trailing spaces    ";  
// Displays "    leading and trailing spaces     (35)"  
window.alert(s + " (" + s.length + ")");  
// Remove the leading and trailing spaces  
s = s.trim();  
// Displays "leading and trailing spaces (27)"  
window.alert(s + " (" + s.length + ")");  
```  
  
### <a name="using-prototypes-to-derive-one-object-from-another-with-objectcreate"></a>プロトタイプを使用して Object.create でオブジェクトから別のオブジェクトを派生する  

プロトタイプ `Object` を使用して、あるオブジェクトから別のオブジェクトを派生させることができます。 たとえば、[Object.create](../../javascript/reference/object-create-function-javascript.md) 関数を使用して、前に定義した `Vehicle` オブジェクトのプロトタイプ (および必要な新しいプロパティ) を使用する新しいオブジェクト `Bicycle` を派生させることができます。  
  
```JavaScript  
var bicycle = Object.create(Object.getPrototypeOf(Vehicle), {  
    "pedals" :{value: true}  
});  
  
```  
  
 `bicycle` オブジェクトにはプロパティ `wheels`、`engine`、`color`、および `pedals` があり、そのプロトタイプは `Vehicle.prototype` です。 JavaScript エンジンは `pedals` の `bicycle` プロパティを検索し、さらにプロトタイプ チェーンを検索して `wheels` の `engine`、`color`、および `Vehicle` の各プロパティを探します。  
  
### <a name="changing-an-objects-prototype"></a>オブジェクトのプロトタイプの変更  
 Internet Explorer 11 では、[__proto\_\_](../../javascript/reference/proto-property-object-javascript.md) プロパティを使用して、オブジェクトまたは関数の内部プロトタイプを新しいプロトタイプに置き換えることができます。 このプロパティを使用した場合、プロトタイプ チェーン内の他のプロパティおよびメソッドと共に、新しいプロトタイプのプロパティおよびメソッドが継承されます。  
  
 次の例は、オブジェクトのプロトタイプを変更する方法を示しています。 この例では、プロトタイプを変更するとオブジェクトの継承されたプロパティがどのように変化するかを示します。  
  
```JavaScript  
function Friend() {  
    this.demeanor = "happy";  
}  
  
function Foe() {  
    this.demeanor = "suspicious";  
}  
  
var friend = new Friend();  
var foe = new Foe();  
  
var player = new Object();  
player.__proto__ = foe;  
  
friend.ally = "Tom";  
  
if (console && console.log) {  
    console.log(player.demeanor === "happy" );      // Returns false  
    console.log(player.demeanor === "suspicious");  // Returns true  
    console.log(player.ally === "Tom");             // Returns false  
    // Turn the foe to a friend.  
    player.__proto__ = friend;  
    console.log(player.demeanor === "happy");       // Returns true  
    console.log(player.demeanor === "suspicious");  // Returns false  
    console.log(player.ally === "Tom");             // Returns true  
}  
```
