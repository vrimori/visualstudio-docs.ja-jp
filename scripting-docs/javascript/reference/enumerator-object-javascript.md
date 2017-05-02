---
title: "Enumerator オブジェクト (JavaScript) | Microsoft Docs"
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
  - "Enumerator"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Enumerator オブジェクト"
ms.assetid: 63f03c21-d58c-47db-a728-4d8d88b0a422
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# Enumerator オブジェクト (JavaScript)
コレクション内の項目を列挙する手段を提供します。  
  
> [!WARNING]
>  このオブジェクトは Internet Explorer でのみサポートされます。[!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリではサポートされません。  
  
## 構文  
  
```  
  
enumObj = new Enumerator([collection])   
```  
  
## パラメーター  
 `enumObj`  
 必須です。`Enumerator` オブジェクトを代入する変数名を指定します。  
  
 `collection`  
 省略可能です。 任意の Collection オブジェクトです。  
  
## 解説  
 コレクションは、コレクション メンバーに直接アクセスできない配列とは異なります。 インデックスを使用する代わりに、配列の場合と同じように、現在の項目のポインターをコレクションの最初の要素または次の要素にのみ移動することができます。  
  
 `Enumerator` オブジェクトでは任意のコレクション メンバーにアクセスすることができ、VBScript の `For...Each` ステートメントと同じように動作します。  
  
## 使用例  
 `Enumerator` オブジェクトの使用方法を次のコードに示します。  
  
```javascript  
var bytesPerGB = 1024 * 1024 * 1024;  
  
var fso = new ActiveXObject("Scripting.FileSystemObject");  
  
document.write(fso.Drives);  
var e = new Enumerator(fso.Drives);  
  
var driveString = "";  
  
e.moveFirst();  
while (e.atEnd() == false)  
{  
    var drv = e.item();  
  
    driveString += drv.Path + " - ";  
  
    if (drv.IsReady){  
        var freeGB = drv.FreeSpace / bytesPerGB;  
        var totalGB = drv.TotalSize / bytesPerGB;  
  
        driveString += freeGB.toFixed(3) + " GB free of ";  
        driveString += totalGB.toFixed(3) + " GB";  
    }  
    else{  
        driveString += "Not Ready";  
    }  
  
    driveString += "<br />";;  
  
    e.moveNext();  
}  
document.write(driveString);  
  
// Output: <drive information  
  
```  
  
## プロパティ  
 `Enumerator` オブジェクトにはプロパティはありません。  
  
## メソッド  
 [atEnd メソッド](../../javascript/reference/atend-method-enumerator-javascript.md) &#124; [item メソッド](../../javascript/reference/item-method-enumerator-javascript.md) &#124; [moveFirst メソッド](../../javascript/reference/movefirst-method-enumerator-javascript.md) &#124; [moveNext メソッド](../../javascript/reference/movenext-method-enumerator-javascript.md)  
  
## 必要条件  
 Quirks、Internet Explorer 6 標準、Internet Explorer 7 標準、Internet Explorer 8 標準、Internet Explorer 9 標準、Internet Explorer 10 標準の各ドキュメント モードでサポートされます。[!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリではサポートされていません。 「[バージョン情報](../../javascript/reference/javascript-version-information.md)」を参照してください。  
  
## 参照  
 [Boolean オブジェクト](../../javascript/reference/boolean-object-javascript.md)