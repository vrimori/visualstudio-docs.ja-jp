---
title: "Debug.write 関数 (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Write
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: write method [JavaScript]
ms.assetid: fd1cfbb3-46cb-47cc-896c-a70d457dd413
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 74aad7a01e0dc166f22173cf193b312e1fd4d804
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="debugwrite-function-javascript"></a>Debug.write 関数 (JavaScript)
文字列をスクリプト デバッガーに送信します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Debug.write([str1 [, str2 [, ... [, strN]]]])  
```  
  
## <a name="parameters"></a>パラメーター  
 *str1、…、str2 strN*  
 省略可能です。 スクリプト デバッガーに送信する文字列。  
  
## <a name="remarks"></a>コメント  
 `Debug.write`関数は、実行時にスクリプト デバッガーのイミディ エイト ウィンドウに文字列を送信します。 スクリプトがデバッグされない場合、`Debug.write`関数も何も起こりません。  
  
 `Debug.write`関数はほぼ同じである、`Debug.writeln`関数。 唯一の違いは、`Debug.writeln`関数は、文字列が送信された後に改行文字を送信します。  
  
## <a name="example"></a>例  
 この例では、`Debug.write`スクリプト デバッガーのイミディ エイト ウィンドウで、変数の値を表示する関数。  
  
> [!NOTE]
>  この例を実行するには、スクリプト デバッガーをインストールが必要し、スクリプトがデバッグ モードで実行する必要があります。  
>   
>  Internet Explorer 8 が含まれています、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]デバッガーです。 以前のバージョンの Internet Explorer を使用している場合は、「 [方法 : Internet Explorer でスクリプトのデバッグを有効にして起動する](http://go.microsoft.com/fwlink/?LinkId=133801)」をご覧ください。  
  
```JavaScript  
var counter = 42;  
Debug.write("The value of counter is " + counter);  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用されます**: [Debug オブジェクト](../../javascript/reference/debug-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [Debug.writeln 関数](../../javascript/reference/debug-writeln-function-javascript.md)