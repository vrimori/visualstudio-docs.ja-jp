---
title: "Boolean オブジェクト (JavaScript) | Microsoft Docs"
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
  - "boolean_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Boolean データ型, Boolean オブジェクト"
  - "Boolean オブジェクト"
ms.assetid: d67748f2-7bf5-4889-8269-e777616cc5f0
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Boolean オブジェクト (JavaScript)
新しいブール値を作成します。  
  
## 構文  
  
```  
  
boolObj = new Boolean([boolValue])  
```  
  
## パラメーター  
 `boolObj`  
 必須です。  `Boolean` オブジェクトを代入する変数名を指定します。  
  
 `boolValue`  
 省略可能です。  新しいオブジェクトの初期ブール値を指定します。  `boolvalue` を省略するか、`false`、0、`null`、`NaN`、または空の文字列のいずれかを指定すると、Boolean オブジェクトの初期値は`false` になります。  それ以外の場合、初期値は `true` になります。  
  
## 解説  
 `Boolean` オブジェクトは、Boolean 型のラッパーです。  [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] は、ブール型が `Boolean` オブジェクトに変換されると、暗黙的に `Boolean` オブジェクトを使用します。  
  
 `Boolean` オブジェクトのインスタンスを明示的に作成することはほとんどありません。  
  
## プロパティ  
 `Boolean` オブジェクトのプロパティを次の表に示します。  
  
|プロパティ|説明|  
|-----------|--------|  
|[constructor プロパティ](../../javascript/reference/constructor-property-boolean.md)|ブール値を作成する関数を指定します。|  
|[prototype プロパティ](../../javascript/reference/prototype-property-boolean.md)|ブール型のプロトタイプへの参照を返します。|  
  
<a name="js56jsobjarraymeth"></a>   
## メソッド  
 `Boolean` オブジェクトのメソッドを次の表に示します。  
  
|メソッド|説明|  
|----------|--------|  
|[toString メソッド](../../javascript/reference/tostring-method-boolean-1.md)|ブール値の文字列表現を返します。|  
|[valueOf メソッド](../../javascript/reference/valueof-method-boolean.md)|ブール値への参照を取得します。|  
  
## 必要条件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]