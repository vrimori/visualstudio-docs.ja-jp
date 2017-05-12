---
title: "正規表現の中に &#39;)&#39; が必要です (JavaScript) | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5020"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# 正規表現の中に &#39;)&#39; が必要です (JavaScript)
正規表現のキャプチャ、アサーション、またはグループを作成しようとしましたが右かっこが含まれていません。  正規表現では、いろいろな目的でかっこが使用されます。  主に、サブ式のキャプチャ、アサーションの指定、またはパターンのグループ化に使用され、\*、\+、? などによって項目を単一の単位として処理できるようにします。  
  
### このエラーを解決するには  
  
-   一番右の右かっこを追加します。  
  
    > [!NOTE]
    >  単一のかっこと一致させる場合は、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] で特殊文字と解釈されないように、円記号でエスケープして \\\( とします。  
  
## 参照  
 [Regular Expression オブジェクト](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/ja-jp/ab0766e1-7037-45ed-aa23-706f58358c0e)