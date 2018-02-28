---
title: "moveFirst メソッド (Enumerator) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- moveFirst
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- MoveFirst method
ms.assetid: 96eedc66-7974-443c-b0cd-55373a7c0e59
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: af8c59194a5655730e8509b43533f699aeef51d2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="movefirst-method-enumerator-javascript"></a>moveFirst メソッド (Enumerator) (JavaScript)
コレクション内の現在の項目を最初の項目にリセットします。  
  
> [!WARNING]
>  このオブジェクトは、Internet Explorer でのみサポートされます。  
  
## <a name="syntax"></a>構文  
  
```  
  
enumObj.moveFirst( )   
```  
  
## <a name="remarks"></a>コメント  
 必要な *enumObj* 参照は任意の `Enumerator` オブジェクトです。  
  
 コレクション内に項目がない場合は、現在の項目が未定義に設定されます。  
  
## <a name="example"></a>例  
 次の例では、リストの先頭から `moveFirst` コレクションのメンバーを評価するために `Drives` メソッドが使用されています。  
  
```JavaScript  
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
  
## <a name="requirements"></a>要件  
 Quirks、Internet Explorer 6 標準、Internet Explorer 7 標準、Internet Explorer 8 標準、Internet Explorer 9 標準、Internet Explorer 10 標準の各ドキュメント モードでサポートされます。 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリではサポートされていません。 「 [バージョン情報](../../javascript/reference/javascript-version-information.md)」を参照してください。  
  
 **適用対象**: [Enumerator Object](../../javascript/reference/enumerator-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [atEnd メソッド (Enumerator)](../../javascript/reference/atend-method-enumerator-javascript.md)   
 [item メソッド (Enumerator)](../../javascript/reference/item-method-enumerator-javascript.md)   
 [moveNext メソッド (Enumerator)](../../javascript/reference/movenext-method-enumerator-javascript.md)