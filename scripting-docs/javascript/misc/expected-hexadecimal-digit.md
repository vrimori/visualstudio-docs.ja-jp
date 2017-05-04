---
title: "16 進数の数字が必要です。 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1023"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 67a86df7-49f9-43cb-99c6-99b1a427827a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 16 進数の数字が必要です。
不適切な Unicode エスケープ シーケンスを作成しました。  Unicode エスケープ シーケンスは \\u で始まり、その後に必ず 4 桁の 16 進数が続きます。  Unicode の 16 進数の各桁に使用できるのは、数字の 0 ～ 9、大文字の A ～ F、小文字の a ～ f だけです。  正しい形式の Unicode エスケープ シーケンスの例を次に示します。  
  
```javascript  
z = "\u1A5F";  
```  
  
### このエラーを解決するには  
  
-   Unicode 16 進数が \\u で始まり、各桁に数字の 0 ～ 9、大文字の A ～ F、小文字の a ～ f のみが含まれ、4 桁にまとまっていることを確認してください。  
  
    > [!NOTE]
    >  文字列にリテラル テキスト \\u を使用する場合は、円記号を 2 つ \(\\\\u\) を使用します。1 つは最初の円記号をエスケープするために使用されます。  
  
## 参照  
 [データ型](../../javascript/data-types-javascript.md)