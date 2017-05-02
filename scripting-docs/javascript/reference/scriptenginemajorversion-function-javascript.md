---
title: "ScriptEngineMajorVersion 関数 (JavaScript) | Microsoft Docs"
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
  - "ScriptEngineMajorVersion"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ScriptEngineMajorVersion 関数"
ms.assetid: 3e251bce-1e14-4cb5-b79f-53845d1920fd
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# ScriptEngineMajorVersion 関数 (JavaScript)
使用されているスクリプト エンジンのメジャー バージョン番号を取得します。  
  
## 構文  
  
```  
ScriptEngineMajorVersion()  
```  
  
## 解説  
 返り値は、使用されているスクリプト言語のダイナミック リンク ライブラリ \(DLL\) に含まれているバージョン情報に直接対応しています。  
  
## 使用例  
 `ScriptEngineMajorVersion` 関数の使用例を次に示します。  
  
```javascript  
if (window.ScriptEngineMajorVersion) {  
    console.log(window.ScriptEngine());   
}  
  
Output: <current major version>  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## 参照  
 [ScriptEngine 関数](../../javascript/reference/scriptengine-function-javascript.md)   
 [ScriptEngineBuildVersion 関数](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [ScriptEngineMinorVersion 関数](../../javascript/reference/scriptengineminorversion-function-javascript.md)