---
title: moveNext メソッド (Enumerator) (JavaScript) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- moveNext
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- MoveNext method
ms.assetid: 59aa339b-f375-450a-8276-37896a55a824
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab9b07a9a9c4640407cff0eaf21a6e8cd65dac11
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639772"
---
# <a name="movenext-method-enumerator-javascript"></a>moveNext メソッド (Enumerator) (JavaScript)
コレクション内の現在の項目を次の項目に移動します。  
  
> [!WARNING]
>  このオブジェクトは、Internet Explorer でのみサポートされます。  
  
## <a name="syntax"></a>構文  
  
```  
  
enumObj.moveNext( )   
```  
  
## <a name="remarks"></a>コメント  
 必要な *enumObj* 参照は任意の `Enumerator` オブジェクトです。  
  
 列挙子がコレクションの末尾にあるか、コレクションが空である場合は、現在の項目が未定義に設定されます。  
  
## <a name="example"></a>例  
 次の例では、 **コレクション内の次のドライブに移動するために** moveNext `Drives` メソッドが使用されています。  
  
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
 [moveFirst メソッド (Enumerator)](../../javascript/reference/movefirst-method-enumerator-javascript.md)