---
title: "エンコードする URI は無効な文字を含んでいます。 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5024"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# エンコードする URI は無効な文字を含んでいます。
文字列を URI （Uniform Resource Identifier） としてエンコードしようとしましたが、無効な文字が含まれていました。  文字列内のほとんどの文字が URI に変換できる有効な文字ですが、一部の Unicode 文字シーケンスは無効です。  
  
### このエラーを解決するには  
  
-   エンコードされる文字列に、有効な Unicode 表記のみが含まれていることを確認します。  完全な URI は、コンポーネントと区切り記号のシーケンスで構成されます。  山かっこの中の名前はコンポーネントを表し、":"、"\/"、";"、"?" の各文字は区切り記号として使用される予約文字です。  一般的な書式は次のとおりです。  
  
    ```javascript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## 参照  
 [encodeURI 関数](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeURIComponent 関数](../../javascript/reference/encodeuricomponent-function-javascript.md)