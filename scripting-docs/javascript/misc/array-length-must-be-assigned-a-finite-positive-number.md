---
title: "配列の長さには、正の有限数が割り当てられなければなりません。 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5030"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: c51c66a4-a543-4e95-b18d-2cfbcb3d1fdd
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 配列の長さには、正の有限数が割り当てられなければなりません。
既存の **Array** オブジェクトの **length** プロパティを設定する際に、正の整数またはゼロ以外の配列の長さを指定しました。  このエラーは、`Array` オブジェクトの **length** プロパティに負の数値または数値ではない値 \(`NaN`\) を割り当てると発生します。  [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] では、小数は自動的に整数に変換されます。  
  
### このエラーを解決するには  
  
-   length プロパティには正の整数を割り当てます。  配列サイズに上限はありませんが、整数の最大値の制限があります \(約 40 億\)。  **Array** オブジェクトの **length** プロパティを正しく設定する方法の例を次に示します。  
  
    ```javascript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## 参照  
 [配列の使用](../../javascript/advanced/using-arrays-javascript.md)