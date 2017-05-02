---
title: "use strict ディレクティブ | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "strict_JavaScriptKeyword"
  - "use strict"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "厳格モード"
  - "use strict ディレクティブ"
  - "use strict"
ms.assetid: b532e8c9-548c-4bbe-b2fc-5459ebd62e56
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# use strict ディレクティブ
JavaScript の一部の機能の使用を制限します。  Internet Explorer 10 と [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリでのみサポートされます。  
  
## 構文  
  
```javascript  
use strict  
```  
  
## 解説  
  
## 使用例  
 厳格モードではすべての変数を `var` で宣言する必要があるので、次のコードでは構文エラーが発生します。  
  
```javascript  
"use strict";  
function testFunction(){  
   var testvar = 4;  
    return testvar;  
}  
intvar = 5;  
  
```  
  
## 参照  
 [厳格モード](../../javascript/advanced/strict-mode-javascript.md)