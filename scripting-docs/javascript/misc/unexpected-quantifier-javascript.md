---
title: "予期しない量指定子です (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5018"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# 予期しない量指定子です (JavaScript)
正規表現検索パターンを作成する際に、無効な量化子を使用してパターン要素を作成しました。  パターンの例を次に示します。  
  
```  
/^+/  
```  
  
 このパターンの要素 （^ \(入力の先頭\)） に量化子は指定できないので無効です。  量化子を指定できない要素の一覧を次の表に示します。  
  
|要素|説明|  
|--------|--------|  
|^|入力の先頭|  
|$|入力の末尾|  
|\\b|ワード境界|  
|\\B|ワード境界以外|  
|\*|0 回以上の繰り返し|  
|\+|1 回以上の繰り返し|  
|?|0 回または 1 回の繰り返し|  
|{n}|n 回の繰り返し|  
|{n,}|n 回以上の繰り返し|  
|{n,m}|n 回以上 m 回以下の繰り返し|  
  
### このエラーを解決するには  
  
-   検索パターンの要素に有効な量化子だけが含まれていることを確認します。  
  
## 参照  
 [Regular Expression オブジェクト](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/ja-jp/ab0766e1-7037-45ed-aa23-706f58358c0e)