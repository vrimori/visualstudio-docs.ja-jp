---
title: "ScriptEngineMinorVersion 関数 (JavaScript) | Microsoft Docs"
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
  - "ScriptEngineMinorVersion"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ScriptEngineMinorVersion 関数"
ms.assetid: caa506a5-e61d-4b2a-8b83-83d56a2f26cd
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# ScriptEngineMinorVersion 関数 (JavaScript)
使用されているスクリプト エンジンのマイナー バージョン番号を取得します。  
  
## 構文  
  
```  
ScriptEngineMinorVersion()  
```  
  
## 解説  
 返り値は、使用されているスクリプト言語のダイナミック リンク ライブラリ \(DLL\) に含まれているバージョン情報に直接対応しています。  
  
## 使用例  
 `ScriptEngineMinorVersion` 関数の使用例を次に示します。  
  
```javascript  
if (window.ScriptEngineMinorVersion) {  
    console.log(window.ScriptEngineMinorVersion());  
}  
  
//Output: <current minor version>  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## 参照  
 [ScriptEngine 関数](../../javascript/reference/scriptengine-function-javascript.md)   
 [ScriptEngineBuildVersion 関数](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [ScriptEngineMajorVersion 関数](../../javascript/reference/scriptenginemajorversion-function-javascript.md)