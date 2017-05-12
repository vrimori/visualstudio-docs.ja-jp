---
title: "デコードする URI は正しくエンコードされていません。 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5025"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 029e0790-ffd1-496d-8700-3b3dbac1b6fd
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# デコードする URI は正しくエンコードされていません。
書式が正しくない URI \(Uniform Resource Identifier\) をデコードしようとしました。  URI には特別な構文があり、英数字以外の大半の文字は、URI で使用するにはかっこで囲む必要があります。  `encodeURI` メソッドと `encodeURIComponent` メソッドを使用して、通常の [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 文字列から URI を作成できます。  
  
 完全な URI は、コンポーネントと区切り記号のシーケンスで構成されます。  一般的な書式は次のとおりです。  
  
```javascript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 山かっこの中の名前はコンポーネントを表し、":"、"\/"、";"、"?" の各文字は区切り記号として使用される予約文字です。  
  
### このエラーを解決するには  
  
-   有効な URI だけをデコードするようにします。  無効な文字が含まれる可能性があるため、通常の [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 文字列はデコードできません。  
  
## 参照  
 [decodeURI 関数](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent 関数](../../javascript/reference/decodeuricomponent-function-javascript.md)