---
title: "WinRTError オブジェクト (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "JavaScript, WinRTError オブジェクト"
  - "WinRTError オブジェクト [JavaScript]"
ms.assetid: d75ab8e5-e729-4d86-90fd-ea228c30dd66
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# WinRTError オブジェクト (JavaScript)
Windows ランタイム呼び出しが、失敗を示す HRESULT を返すと、JavaScript はこれを特別な Windows ランタイム エラーに変換します。  これは、Windows ランタイムが使用可能な場合に、グローバルな JavaScript 名前空間の一部として [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリでのみ使用可能です。  
  
## 構文  
  
```  
  
errorObj = new WinRTError();   
```  
  
## 解説  
 WinRTError エラー タイプは、Windows ランタイム API に由来するエラーにのみ使用されます。  
  
## 使用例  
 次の例は、WinRTError がスローされキャッチされる方法を示します。  
  
```javascript  
try {  
            Windows.Storage.ApplicationData.localFolder.createFileAsync("sample.txt");  
        } catch (err) {  
            var n = err;  
        }  
  
```  
  
## メソッド  
 WinRTError オブジェクトにメソッドはありません。  
  
## プロパティ  
 WinRTError オブジェクトのプロパティは、[Error オブジェクト](../../javascript/reference/error-object-javascript.md) オブジェクトと同じです。  
  
## 必要条件  
 WinRTError オブジェクトは、Internet Explorer ではなく [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリでのみサポートされます。  
  
## 参照  
 [Error オブジェクト](../../javascript/reference/error-object-javascript.md)