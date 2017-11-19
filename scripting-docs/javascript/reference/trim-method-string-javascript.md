---
title: "trim メソッド (String) (JavaScript) |Microsoft ドキュメント"
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
helpviewer_keywords: trim method
ms.assetid: 03d38c7e-25cd-4ede-b58e-1a10b5249bab
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de358981cfbf569ef35be95b55b3e9856027df35
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="trim-method-string-javascript"></a>trim メソッド (String) (JavaScript)
文字列から先頭および末尾の空白と行終端記号の文字を削除します。  
  
## <a name="syntax"></a>構文  
  
```  
  
stringObj.trim()  
```  
  
## <a name="parameters"></a>パラメーター  
 `stringObj`  
 必須です。 `String` オブジェクトまたは文字列リテラル。 この文字列は、`trim` メソッドでは変更されません。  
  
## <a name="return-value"></a>戻り値  
 元の文字列から先頭および末尾の空白と行終端記号の文字を削除した文字列。  
  
## <a name="remarks"></a>コメント  
 削除される文字には、空白、タブ、フォーム フィード、キャリッジ リターン、ライン フィードが含まれます。 参照してください[特殊文字](../../javascript/advanced/special-characters-javascript.md)空白と行終端記号の文字の包括的な一覧についてはします。  
  
 例については、独自のトリム メソッドを実装する方法を示す、次を参照してください。[プロトタイプおよびプロトタイプの継承](../../javascript/advanced/prototypes-and-prototype-inheritance.md)です。  
  
## <a name="example"></a>例  
 `trim` メソッドの使用例を次に示します。  
  
```JavaScript  
var message = "    abc def     \r\n  ";  
  
document.write("[" + message.trim() + "]");  
document.write("<br/>");  
document.write("length: " + message.trim().length);  
  
// Output:  
//  [abc def]  
//  length: 7  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [特殊文字](../../javascript/advanced/special-characters-javascript.md)   
 [String オブジェクト](../../javascript/reference/string-object-javascript.md)   
 [スクロール、パン、ズームのサンプル アプリ](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)