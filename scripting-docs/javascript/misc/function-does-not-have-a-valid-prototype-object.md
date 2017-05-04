---
title: "関数には、有効なプロトタイプ オブジェクトが存在しません。 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5023"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# 関数には、有効なプロトタイプ オブジェクトが存在しません。
**instanceof** 演算子を使用して、オブジェクトが特定の関数クラスから派生したかどうかを調べようとしましたが、オブジェクトの `prototype` プロパティを `null` または外部オブジェクト型として再定義しました \(両者とも有効な [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] オブジェクトではありません\)。  外部オブジェクトは、ホスト オブジェクト モデルのオブジェクト \(Internet Explorer のドキュメントやウィンドウ オブジェクトなど\) または外部 COM オブジェクトです。  
  
### このエラーを解決するには  
  
-   関数の `prototype` プロパティが、有効な [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] オブジェクトを参照するようにします。  
  
## 参照  
 [Function オブジェクト](../../javascript/reference/function-object-javascript.md)   
 [prototype プロパティ \(Object\)](../../javascript/reference/prototype-property-object-javascript.md)