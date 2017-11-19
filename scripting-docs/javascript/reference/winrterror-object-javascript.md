---
title: "WinRTError オブジェクト (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- WinRTError object [JavaScript]
- JavaScript, WinRTError object
ms.assetid: d75ab8e5-e729-4d86-90fd-ea228c30dd66
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 11b339b4fc3c4bd4f34416ffd98b8f9c3f288f98
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="winrterror-object-javascript"></a>WinRTError オブジェクト (JavaScript)
Windows ランタイム呼び出しが、失敗を示す HRESULT を返すと、JavaScript はこれを特別な Windows ランタイム エラーに変換します。 これは、Windows ランタイムが使用可能な場合に、グローバルな JavaScript 名前空間の一部として [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリでのみ使用可能です。  
  
## <a name="syntax"></a>構文  
  
```  
  
errorObj = new WinRTError();  
  
```  
  
## <a name="remarks"></a>コメント  
 WinRTError エラー タイプは、Windows ランタイム API に由来するエラーにのみ使用されます。  
  
## <a name="example"></a>例  
 次の例は、WinRTError がスローされキャッチされる方法を示します。  
  
```JavaScript  
try {  
            Windows.Storage.ApplicationData.localFolder.createFileAsync("sample.txt");  
        } catch (err) {  
            var n = err;  
        }  
  
```  
  
## <a name="methods"></a>メソッド  
 WinRTError オブジェクトにメソッドはありません。  
  
## <a name="properties"></a>プロパティ  
 WinRTError オブジェクトと同じプロパティを持つ、[エラー オブジェクト](../../javascript/reference/error-object-javascript.md)オブジェクト。  
  
## <a name="requirements"></a>要件  
 WinRTError オブジェクトは、Internet Explorer ではなく [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリでのみサポートされます。  
  
## <a name="see-also"></a>関連項目  
 [Error オブジェクト](../../javascript/reference/error-object-javascript.md)