---
title: "条件付きコンパイルは無効になっています。 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1030"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 条件付きコンパイルは無効になっています。
条件付きコンパイルを有効にせずに条件付きコンパイル変数を使用しようとしました。  条件付きコンパイルを有効にすると、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] コンパイラにより、@ で始まる識別子が条件付きコンパイル変数として解釈されます。  これを行うには、条件付きコードを次のステートメントで開始します。  
  
```  
/*@cc_on @*/  
```  
  
### このエラーを解決するには  
  
-   次のステートメントを条件付きコードの先頭に追加します。  
  
    ```javascript  
    /*@cc_on @*/  
    ```  
  
## 参照  
 [条件付きコンパイル](../../javascript/advanced/conditional-compilation-javascript.md)   
 [条件付きコンパイル変数](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc\_on ステートメント](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if ステートメント](../../javascript/reference/at-if-statement-javascript.md)   
 [@set ステートメント](../../javascript/reference/at-set-statement-javascript.md)