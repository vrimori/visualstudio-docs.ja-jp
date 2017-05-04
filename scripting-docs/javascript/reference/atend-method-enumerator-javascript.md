---
title: "atEnd メソッド (Enumerator) (JavaScript) | Microsoft Docs"
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
  - "atEnd"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "atEnd メソッド"
ms.assetid: 326808fb-9a0f-428e-aff1-b11b237913f1
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# atEnd メソッド (Enumerator) (JavaScript)
列挙子がコレクションの末尾にあるかどうかを示すブール値を返します。  
  
> [!WARNING]
>  このオブジェクトは、Internet Explorer でのみサポートされます。  
  
## 構文  
  
```  
  
myEnum.atEnd()  
```  
  
## 解説  
 必要な *myEnum* 参照は任意の `Enumerator` オブジェクトです。  
  
 `atEnd` メソッドは、現在の項目がコレクション内の最後の項目である場合、コレクションが空である場合、または現在の項目が未定義の場合に **true** を返します。 それ以外の場合は **false** を返します。  
  
## 使用例  
 次のコードでは、ドライブ リストの最後に達したかどうかを判断するために `atEnd` メソッドが使用されています。  
  
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
 [item メソッド \(Enumerator\)](../../javascript/reference/item-method-enumerator-javascript.md)   
 [moveFirst メソッド \(Enumerator\)](../../javascript/reference/movefirst-method-enumerator-javascript.md)   
 [moveNext メソッド \(Enumerator\)](../../javascript/reference/movenext-method-enumerator-javascript.md)   
 [Enumerator オブジェクト](../../javascript/reference/enumerator-object-javascript.md)