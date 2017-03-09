---
title: "&lt;非推奨&gt; (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cf33d371-59da-4310-95ee-d7524fd9d58c
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;非推奨&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

非推奨の関数またはメソッドを指定します。  
  
## 構文  
  
```  
<deprecated  
    type="deprecate|remove"  
    locid="descriptionID">description  
</deprecated>  
```  
  
#### パラメーター  
 `type`  
 省略可能。  関数またはメソッドが将来のリリースで削除されるかどうか、または関数またはメソッドが既に削除されていて、使用するとエラーが発生することがあるかどうかを指定します。  関数またはメソッドが将来のリリースで削除されることを指定するには、`deprecate` に設定します。  関数またはメソッドが既に削除されたことを指定するには、`remove` に設定します。  
  
 `locid`  
 省略可能。  関数またはメソッドに関するローカライズ情報用の識別子。  この識別子は、メンバーの ID であるか、または OpenAjax のメタデータで定義されているメッセージ バンドル内の `name` 属性値に対応します。  この識別子の型は、[\<loc\>](../ide/loc-javascript.md) 要素で指定された形式によって異なります。  
  
 `description`  
 省略可能。  非推奨になる関数またはメソッドの説明。  
  
## 解説  
 `<deprecated>` など、関数の注釈に使用される要素は、ステートメントの前の関数本体に配置する必要があります。  非推奨として関数にマークを付けるときは、その [\<summary\>](../ide/summary-javascript.md) 要素を `<deprecated>` 要素と置き換えることをお勧めします。  
  
## 使用例  
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
  
## 参照  
 [XML ドキュメント コメント](../ide/xml-documentation-comments-javascript.md)