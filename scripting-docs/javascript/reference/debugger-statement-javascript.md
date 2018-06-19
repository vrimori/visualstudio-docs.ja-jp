---
title: デバッガーのステートメント (JavaScript) |Microsoft ドキュメント
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
- debugger_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- debugger statement
ms.assetid: c6d2e193-c1f7-4fb3-8a4e-cc9823174ae4
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e64e860cebd065f357857484e932b4aea3f05ea
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636202"
---
# <a name="debugger-statement-javascript"></a>debugger ステートメント (JavaScript)
実行を中断します。  
  
## <a name="syntax"></a>構文  
  
```  
debugger  
```  
  
## <a name="remarks"></a>コメント  
 配置できる`debugger`ステートメントの実行を中断するプロシージャに任意の場所。 使用して、`debugger`ステートメントは、コードでブレークポイントの設定に似ています。  
  
 `debugger`ステートメントが実行を中断しますが、任意のファイルを閉じてまたは任意の変数をオフにしません。  
  
> [!NOTE]
>  `debugger`ステートメント及ぼしませんしない限り、スクリプトをデバッグします。  
  
## <a name="example"></a>例  
 この例では、`debugger`ステートメントの各繰り返しの実行を中断、`for`ループします。  
  
> [!NOTE]
>  この例を実行するには、スクリプト デバッガーをインストールが必要し、スクリプトがデバッグ モードで実行する必要があります。  
>   
>  Internet Explorer 8 が含まれています、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]デバッガーです。 以前のバージョンの Internet Explorer を使用している場合は、「 [方法 : Internet Explorer でスクリプトのデバッグを有効にして起動する](http://go.microsoft.com/fwlink/?LinkId=133801)」をご覧ください。  
  
```JavaScript  
for(i = 1; i<5; i++) {  
   // Print i to the Output window.  
   Debug.write("loop index is " + i);  
   // Wait for user to resume.  
   debugger  
}  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [JavaScript ステートメント](../../javascript/reference/javascript-statements.md)   
 [条件付きコンパイル](../../javascript/advanced/conditional-compilation-javascript.md)