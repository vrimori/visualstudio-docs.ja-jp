---
title: "正規表現の中に &#39;]&#39; が必要です (JavaScript) | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5019"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# 正規表現の中に &#39;]&#39; が必要です (JavaScript)
正規表現検索用の文字クラスを作成しようとしましたが、右角かっこが含まれていません。  個々のリテラル文字の組み合わせを角かっこで囲んで文字クラスを構成できます。  文字クラスでは、その中の 1 文字と一致させることができます。  たとえば、\/\[abc\]\/ は、"a"、"b"、"c" のいずれかと一致します。  
  
### このエラーを解決するには  
  
-   正規表現に右角かっこを追加します。  
  
    > [!NOTE]
    >  単一の角かっこと一致させる場合は、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] で特殊文字と解釈されないように、円記号でエスケープして \\\[ とします。  
  
## 参照  
 [Regular Expression オブジェクト](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/ja-jp/ab0766e1-7037-45ed-aa23-706f58358c0e)