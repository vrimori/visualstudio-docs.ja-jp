---
title: "moveFirst メソッド (Enumerator) (JavaScript) | Microsoft Docs"
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
  - "moveFirst"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "MoveFirst メソッド"
ms.assetid: 96eedc66-7974-443c-b0cd-55373a7c0e59
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# moveFirst メソッド (Enumerator) (JavaScript)
コレクション内の現在の項目を最初の項目にリセットします。  
  
> [!WARNING]
>  このオブジェクトは、Internet Explorer でのみサポートされます。  
  
## 構文  
  
```  
  
enumObj.moveFirst( )  
```  
  
## 解説  
 必要な *enumObj* 参照は任意の `Enumerator` オブジェクトです。  
  
 コレクション内に項目がない場合は、現在の項目が未定義に設定されます。  
  
## 使用例  
 次の例では、リストの先頭から `Drives` コレクションのメンバーを評価するために `moveFirst` メソッドが使用されています。  
  
```javascript  
function ShowDrives()  
{  
    var s = "";  
    var bytesPerGB = 1024 * 1024 * 1024;  
  
    var fso = new ActiveXObject("Scripting.FileSystemObject");  
    var e = new Enumerator(fso.Drives);  
  
    e.moveFirst();  
    while (e.atEnd() == false)  
    {  
        var drv = e.item();  
  
        s += drv.Path + " - ";  
  
        if (drv.IsReady)  
        {  
            var freeGB = drv.FreeSpace / bytesPerGB;  
            var totalGB = drv.TotalSize / bytesPerGB;  
  
            s += freeGB.toFixed(3) + " GB free of ";  
            s += totalGB.toFixed(3) + " GB";  
        }  
        else  
        {  
            s += "Not Ready";  
        }  
  
        s += "<br />";  
  
        e.moveNext();  
    }  
    return(s);  
}  
```  
  
## 必要条件  
 Quirks、Internet Explorer 6 標準、Internet Explorer 7 標準、Internet Explorer 8 標準、Internet Explorer 9 標準、Internet Explorer 10 標準の各ドキュメント モードでサポートされます。[!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリではサポートされていません。 「[バージョン情報](../../javascript/reference/javascript-version-information.md)」を参照してください。  
  
 **適用対象**: [Enumerator オブジェクト](../../javascript/reference/enumerator-object-javascript.md)  
  
## 参照  
 [atEnd メソッド \(Enumerator\)](../../javascript/reference/atend-method-enumerator-javascript.md)   
 [item メソッド \(Enumerator\)](../../javascript/reference/item-method-enumerator-javascript.md)   
 [moveNext メソッド \(Enumerator\)](../../javascript/reference/movenext-method-enumerator-javascript.md)