---
title: "&#39;@&#39; が必要です。 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1032"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 82ff8b74-1710-4358-9a26-dc92ab29c53b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# &#39;@&#39; が必要です。
`@set` ステートメントを使用して条件付きコンパイルのステートメントで使用する変数を作成しようとしましたが、変数名の前にアット マーク \(**@**\) を記述しませんでした。  
  
### このエラーを解決するには  
  
-   変数名の直前にアット マーク \(**@**\) を追加してください。  次に例を示します。  
  
    ```javascript  
    @set @myvar = 1  
    ```  
  
## 参照  
 [@set ステートメント](../../javascript/reference/at-set-statement-javascript.md)   
 [条件付きコンパイル](../../javascript/advanced/conditional-compilation-javascript.md)   
 [条件付きコンパイル変数](../../javascript/advanced/conditional-compilation-variables-javascript.md)