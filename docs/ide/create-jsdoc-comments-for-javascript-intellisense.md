---
title: "JavaScript IntelliSense の JSDoc コメントを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a0dadc81-3755-4a47-bcee-c1010819ff2a
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# JavaScript IntelliSense の JSDoc コメントを作成する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

IntelliSense in Visual Studio は、標準的な JSDoc コメントを使用してスクリプトに追加する情報を表示します。  JSDoc コメントを使用すると、関数、フィールド、変数などのコード要素についての情報を指定できます。  
  
## JSDoc コメント用のタグ  
 次の標準的な JSDoc コメント タグは、コードについての情報を表示するために IntelliSense によって使用されます。  
  
|JSDoc タグ|構文|ノート|  
|--------------|--------|---------|  
|@deprecated|@deprecated *description*|非推奨の関数またはメソッドを指定します。|  
|@description|@description *description*|関数またはメソッドの説明を指定します。|  
|@param|@param {*type*} *parameterName**description*|関数またはメソッドのパラメーターの情報を指定します。<br /><br /> TypeScript でも、@paramTag をサポートしています。|  
|@property|@property {*type*} *propertyName*|オブジェクトで定義されているフィールドまたはメンバーについて、説明を含む情報を指定します。|  
|@returns|@returns {*type*}|戻り値を指定します。<br /><br /> TypeScript では、@returns の代わりに @returnType を使用します。|  
|@summary|@summary *description*|関数またはメソッドの説明を指定します \(@description と同じです\)。|  
|@type|@type {*type*}|定数または変数の種類を指定します。|  
|@typedef|@typedef {*type*} *customTypeName*|カスタム型を指定します。|  
  
### 使用例  
 次の例は、`getArea` という名前の関数について、@description、@param、および @return JSDoc のタグの使用方法を示しています。  
  
```javascript  
/** @description Determines the area of a circle that has the specified radius parameter.  
 * @param {number} radius The radius of the circle.  
 * @return {number}  
 */  
function getArea(radius) {  
    var areaVal;  
    areaVal = Math.PI * radius * radius;  
    return areaVal;  
}  
```  
  
 前の例では、IntelliSense は説明、パラメーター、および `getArea` の始めかっこを入力したときに返す情報を表示します。  
  
 ![関数の IntelliSense の情報](~/docs/ide/media/js_intellisense_jsdoc_comments.png "JS\_IntelliSense\_JSDoc\_Comments")  
  
 次の例は、@typedef タグを @property タグと一緒に使用する方法を示しています。  
  
```javascript  
/**  
  * @typedef {object} Weather  
  * @property {string} current The current weather.  
  */  
function getForecast(Weather) {  
}  
  
var w = new Weather();  
```  
  
 @type JSDoc タグの使用方法を次の例に示します。  この例で示すように、最初のアスタリスクのペア \(\*\*\) の後に続く 1 つのアスタリスク \(\*\) は必須ではありません。  
  
```javascript  
/**  
    @type {string}  
*/  
const RED = 'FF0000';  
  
```  
  
 次の例は、@deprecated JSDoc タグの使用方法を示しています。  
  
```javascript  
/**  
 * @deprecated since version 2.0  
 */  
function old() {  
}  
```