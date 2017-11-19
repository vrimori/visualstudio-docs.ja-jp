---
title: "Debug オブジェクト (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: debug
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Debug object
- Debug object, about Debug object
ms.assetid: 42a367ec-beb1-4e59-8342-34c326eca042
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6286e5db853daa97e43f36a1467abe90cbced5c8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="debug-object-javascript"></a>Debug オブジェクト (JavaScript)
出力をデバッガーに送信する組み込みのグローバル オブジェクトです。  
  
## <a name="syntax"></a>構文  
  
```  
Debug.function  
```  
  
## <a name="remarks"></a>コメント  
 Debug オブジェクトをインスタンス化することはありません。 そのすべてのプロパティおよびメソッドには、 `function`を呼び出してアクセスできます。  
  
 Internet Explorer と [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリのデバッグ方法は異なります。 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリでは、 `write` オブジェクトの `writeln` 関数と `Debug` 関数で、実行時に Visual Studio の **出力** ウィンドウに文字列を表示します。 デバッグの詳細については[!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]アプリを参照してください[デバッグ Windows ユニバーサル アプリの Visual Studio](/visualstudio/debugger/debugging-windows-store-and-windows-universal-apps.md)です。  
  
 Internet Explorer スクリプトをデバッグするには、スクリプト デバッガーをインストールし、スクリプトをデバッグ モードで実行する必要があります。 Internet Explorer 8 以降のバージョンには [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] のデバッガーが含まれます。 以前のバージョンの Internet Explorer を使用している場合は、「 [方法 : Internet Explorer でスクリプトのデバッグを有効にして起動する](http://go.microsoft.com/fwlink/?LinkId=133801)」をご覧ください。  
  
 スクリプトがデバッグされない場合、関数の影響はありません。  
  
## <a name="example"></a>例  
 この例では、 `write` 関数を使用して変数の値を表示します。  
  
```JavaScript  
var counter = 42;  
Debug.write("The value of counter is " + counter);  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="constants"></a>定数  
 [Debug 定数](../../javascript/reference/debug-constants.md)  
  
## <a name="properties"></a>プロパティ  
 [Debug.debuggerEnabled プロパティ](../../javascript/reference/debug-debuggerenabled-property.md)&#124;です。[Debug.setNonUserCodeExceptions プロパティ](../../javascript/reference/debug-setnonusercodeexceptions-property.md)  
  
## <a name="functions"></a>関数  
 [Debug.msTraceAsyncCallbackStarting 関数](../../javascript/reference/debug-mstraceasynccallbackstarting-function.md)&#124;です。[Debug.msTraceAsyncCallbackCompleted 関数](../../javascript/reference/debug-mstraceasynccallbackcompleted-function.md)&#124;です。[Debug.msTraceAsyncOperationCompleted 関数](../../javascript/reference/debug-mstraceasyncoperationcompleted-function.md)&#124;です。[Debug.msTraceAsyncOperationStarting 関数](../../javascript/reference/debug-mstraceasyncoperationstarting-function.md)&#124;です。[Debug.msUpdateAsyncCallbackRelation 関数](../../javascript/reference/debug-msupdateasynccallbackrelation-function.md)&#124;です。[Debug.write 関数](../../javascript/reference/debug-write-function-javascript.md)&#124;です。[Debug.writeln 関数](../../javascript/reference/debug-writeln-function-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [debugger ステートメント](../../javascript/reference/debugger-statement-javascript.md)