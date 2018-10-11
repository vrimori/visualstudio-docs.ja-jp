---
title: JavaScript IntelliSense の JSDoc コメントを作成する |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0dadc81-3755-4a47-bcee-c1010819ff2a
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e24338a75dd631cee86ea8ac81e774e81732bba5
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/09/2018
ms.locfileid: "48878993"
---
# <a name="create-jsdoc-comments-for-javascript-intellisense"></a>JavaScript IntelliSense の JSDoc コメントを作成する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Visual Studio 2017 ドキュメント](/visualstudio/)します。  
  
IntelliSense in Visual Studio は、標準的な JSDoc コメントを使用してスクリプトに追加する情報を表示します。 JSDoc コメントを使用すると、関数、フィールド、変数などのコード要素についての情報を指定できます。  
  
## <a name="jsdoc-comment-tags"></a>JSDoc コメント用のタグ  
 次の標準的な JSDoc コメント タグは、コードについての情報を表示するために IntelliSense によって使用されます。  
  
|JSDoc タグ|構文|メモ|  
|---------------|------------|-----------|  
|@deprecated|@deprecated *説明*|非推奨の関数またはメソッドを指定します。|  
|@description|@description *説明*|関数またはメソッドの説明を指定します。|  
|@param|@param {*型*} *parameterName * * の説明*|関数またはメソッドのパラメーターの情報を指定します。<br /><br /> TypeScript もサポートしています。@paramTagします。|  
|@property|@property {*型*} *propertyName*|オブジェクトで定義されているフィールドまたはメンバーについて、説明を含む情報を指定します。|  
|@returns|@returns {*型*}|戻り値を指定します。<br /><br /> TypeScript を使用して@returnTypeの代わりに@returnsします。|  
|@summary|@summary *説明*|関数またはメソッドの説明を指定します (同じ@description)。|  
|@type|@type {*型*}|定数または変数の種類を指定します。|  
|@typedef|@typedef {*型*} *customTypeName*|カスタム型を指定します。|  
  
### <a name="examples"></a>使用例  
 次の例では、使用、 @description、 @param、および@returnJSDoc タグという名前の関数`getArea`します。  
  
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
  
 ![関数の IntelliSense 情報](../ide/media/js-intellisense-jsdoc-comments.png "JS_IntelliSense_JSDoc_Comments")  
  
 次の例は、使用する方法を示します、@typedefにタグを付ける、@propertyタグ。  
  
```javascript  
/**  
  * @typedef {object} Weather  
  * @property {string} current The current weather.  
  */  
function getForecast(Weather) {  
}  
  
var w = new Weather();  
```  
  
 次の例では、使用、 @type JSDoc タグ。 この例に示すように 1 つのアスタリスク (*)、最初のアスタリスクのペアに続く (\*\*) は必要ありません。  
  
```javascript  
/**  
    @type {string}  
*/  
const RED = 'FF0000';  
  
```  
  
 次の例は、使用する方法を示します、 @deprecated JSDoc タグ。  
  
```javascript  
/**  
 * @deprecated since version 2.0  
 */  
function old() {  
}  
```



