---
title: "配列の長さは、正の有限整数でなければなりません。 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5029"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 1a467040-4702-4178-848f-418a5974e907
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 配列の長さは、正の有限整数でなければなりません。
**Array** コンストラクターを呼び出したときに、0 と正の整数以外の引数を指定しています。  
  
### このエラーを解決するには  
  
-   新しい `Array` オブジェクトを作成する場合は、正の整数だけを使用します。  整数でない要素 1 つだけの配列を作成する場合は、次のように 2 段階のプロセスにします。  最初に要素が 1 つだけの配列を作成し、次に最初の要素 \(array \[0\]\) に値を代入します。  このエラーが発生する例を次に示します。  
  
    ```javascript  
    var piArray = new Array(3.14159);  
    ```  
  
     数値要素が 1 つだけの配列を指定する正しい方法を次に示します。  
  
    ```javascript  
    var piArray = new Array(1);  
    piArray [0] = 3.14159;  
    ```  
  
     配列サイズに上限はありませんが、整数の最大値の制限があります \(約 40 億\)。  
  
## 参照  
 [配列の使用](../../javascript/advanced/using-arrays-javascript.md)