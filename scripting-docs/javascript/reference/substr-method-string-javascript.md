---
title: substr メソッド (String) (JavaScript) |Microsoft ドキュメント
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
- substr
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- substr method
ms.assetid: f12541c1-2623-482e-941d-2e22bc3c4a4a
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b002bfefbeb81c534c882fa4a4720c93ccca185
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640032"
---
# <a name="substr-method-string-javascript"></a>substr メソッド (String) (JavaScript)
指定した位置から、指定した長さの部分文字列を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
stringvar.substr(start [, length ])   
```  
  
## <a name="parameters"></a>パラメーター  
 `stringvar`  
 必須です。 文字列リテラルまたは`String`部分文字列を抽出するオブジェクトします。  
  
 `start`  
 必須です。 目的の部分文字列の開始位置。 文字列の最初の文字のインデックスは 0 です。  
  
 `length`  
 省略可能です。 返された部分文字列に含まれる文字の数。  
  
## <a name="remarks"></a>コメント  
 場合`length`がゼロまたは負の値、空の文字列が返されます。 部分文字列が引き続きの末尾に指定しない場合、`stringvar`です。  
  
## <a name="example"></a>例  
 `substr` メソッドの使用例を次に示します。  
  
```JavaScript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.substr(10, 5);    
document.write("[" + ss + "] <br>");  
  
ss = s.substr(10);  
document.write("[" + ss + "] <br>");  
  
ss = s.substr(10, -5);  
document.write("[" + ss + "] <br>");  
  
// Output:  
// [brown]   
// [brown fox jumps over the lazy dog.]   
// []  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用されます**:[文字列オブジェクト](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [substring メソッド (String)](../../javascript/reference/substring-method-string-javascript.md)