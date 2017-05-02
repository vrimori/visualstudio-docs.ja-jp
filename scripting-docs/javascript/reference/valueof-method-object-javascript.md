---
title: "valueOf メソッド (Object) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "valueOf"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "valueOf メソッド"
ms.assetid: c555e38b-f451-4341-8fcd-4c8b02906a2c
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# valueOf メソッド (Object) (JavaScript)
指定されたオブジェクトのプリミティブ値を返します。  
  
## 構文  
  
```  
  
object.valueOf( )  
```  
  
## 解説  
 必須の `object` 参照には、任意の [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 組み込みオブジェクトを指定します。  
  
 `valueOf` メソッドは、それぞれの [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 組み込みオブジェクトによって異なります。  
  
|Object|戻り値|  
|------------|---------|  
|Array|配列のインスタンスを返します。|  
|Boolean|オブジェクトに格納されているブール値を返します。|  
|Date|世界協定時刻 \(UTC\) の 1970 年 1 月 1 日 0 時 0 分 0 秒からの経過時間を表すミリ秒単位の時刻値。|  
|関数|関数自体を返します。|  
|Number|オブジェクトに格納されている数値を返します。|  
|Object|オブジェクト自体を返します。  これは、既定の設定です。|  
|文字列|オブジェクトに格納されている文字列を返します。|  
  
 **Math** オブジェクトおよび `Error` オブジェクトには、`valueOf` メソッドはありません。  
  
## 必要条件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 **対象**: [Array オブジェクト](../../javascript/reference/array-object-javascript.md)&#124; [Boolean オブジェクト](../../javascript/reference/boolean-object-javascript.md)&#124; [Date オブジェクト](../../javascript/reference/date-object-javascript.md)&#124; [Function オブジェクト](../../javascript/reference/function-object-javascript.md)&#124; [Number オブジェクト](../../javascript/reference/number-object-javascript.md)&#124; [Object オブジェクト](../../javascript/reference/object-object-javascript.md)&#124; [String オブジェクト](../../javascript/reference/string-object-javascript.md)  
  
## 参照  
 [toString メソッド \(Object\)](../../javascript/reference/tostring-method-object-javascript.md)