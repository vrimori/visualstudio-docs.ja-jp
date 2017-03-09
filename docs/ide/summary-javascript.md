---
title: "&lt;summary&gt; (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "summary JavaScript XML タグ"
  - "<summary> JavaScript XML タグ"
ms.assetid: 6540582d-bdb3-42ec-ad2f-c176783e6f9c
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;summary&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

関数またはメソッドの説明を指定します。  
  
## 構文  
  
```  
<summary locid="descriptionID">description  
</summary>  
```  
  
#### パラメーター  
 `locid`  
 省略可能。  関数またはメソッドに関するローカライズ情報用の識別子。  この識別子は、メンバーの ID であるか、または OpenAjax のメタデータで定義されているメッセージ バンドル内の `name` 属性値に対応します。  この識別子の型は、[\<loc\>](../ide/loc-javascript.md) 要素で指定された形式によって異なります。  
  
 `description`  
 省略可能。  関数またはメソッドの説明。  
  
## 解説  
 [\<summary\>](../ide/summary-javascript.md)、[\< param \>](../ide/param-javascript.md)、[\<returns\>](../ide/returns-javascript.md) など、関数の注釈に使用される要素は、ステートメントの前の関数本体に配置する必要があります。  
  
## 使用例  
 次のコードに、`<summary>` 要素を使用する方法を示します。  
  
```javascript  
function areaFunction(radiusParam)  
{  
    /// <summary>Determines the area of a circle when supplied a radius parameter.</summary>  
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>  
    /// <returns type="Number">The area.</returns>  
    var areaVal;  
    areaVal = Math.PI * radiusParam * radiusParam;  
    return areaVal;  
}  
  
```  
  
## 参照  
 [XML ドキュメント コメント](../ide/xml-documentation-comments-javascript.md)