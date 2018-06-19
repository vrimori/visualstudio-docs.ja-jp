---
title: Debug.writeln 関数 (JavaScript) |Microsoft ドキュメント
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
- writeln
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- writeIn method
ms.assetid: c3aad0cd-0486-4161-9ba6-31d672da72af
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 848760e59632b05605de2d73615a2b025df363da
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636282"
---
# <a name="debugwriteln-function-javascript"></a>Debug.writeln 関数 (JavaScript)
文字列を改行文字が続く、スクリプト デバッガーに送信します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Debug.writeln([str1 [, str2 [, ... [, strN]]]])  
```  
  
## <a name="parameters"></a>パラメーター  
 *str1、…、str2 strN*  
 省略可能です。 スクリプト デバッガーに送信する文字列。  
  
## <a name="remarks"></a>コメント  
 `Debug.writeln`関数は実行時に Microsoft Script Debugger のイミディ エイト ウィンドウに、改行文字が続く文字列を送信します。 スクリプトがデバッグされない場合、`Debug.writeln`関数も何も起こりません。  
  
 `Debug.writeln`関数はほぼ同じである、`Debug.write`関数。 唯一の違いは、`Debug.write`関数では、文字列の送信後に改行文字を送信しません。  
  
## <a name="example"></a>例  
 この例では、 `Debug.writeln` Microsoft Script Debugger のイミディ エイト ウィンドウで、変数の値を表示する関数。  
  
> [!NOTE]
>  この例を実行するには、スクリプト デバッガーをインストールが必要し、スクリプトがデバッグ モードで実行する必要があります。  
>   
>  Internet Explorer 8 が含まれています、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]デバッガーです。 以前のバージョンの Internet Explorer を使用している場合は、「 [方法 : Internet Explorer でスクリプトのデバッグを有効にして起動する](http://go.microsoft.com/fwlink/?LinkId=133801)」をご覧ください。  
  
```JavaScript  
var counter = 42;  
Debug.writeln("The value of counter is " + counter);  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用されます**: [Debug オブジェクト](../../javascript/reference/debug-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [Debug.write 関数](../../javascript/reference/debug-write-function-javascript.md)