---
title: "eval 関数 (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: eval
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- eval function
- parsing, code
- parser
ms.assetid: 85587e39-9325-4b75-b9f9-9d7d475a2120
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 388e486f58bb70fd192701060a5faefaed8bd98e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="eval-function-javascript"></a>eval 関数 (JavaScript)
評価[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]コード、実行します。  
  
## <a name="syntax"></a>構文  
  
```  
eval(codeString)   
```  
  
## <a name="parameters"></a>パラメーター  
 `codeString`  
 必須です。 A`String`を含む有効な値[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]コード。  
  
## <a name="remarks"></a>コメント  
 `eval`関数の動的な実行を有効に[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]ソース コードです。  
  
 `codeString`によって文字列が解析、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]パーサーおよび実行します。  
  
 渡される、コード、`eval`への呼び出しと同じコンテキストで関数が実行される、`eval`関数。  
  
 可能な限り、使用、 [JSON.parse 関数](../../javascript/reference/json-parse-function-javascript.md)JavaScript Object Notation (JSON) 文字列を逆シリアル化します。 `JSON.parse`関数がより安全であり、速く実行よりも、`eval`関数。  
  
## <a name="example"></a>例  
 次のコードは、変数を初期化`myDate`テストの日付にします。  
  
```JavaScript  
var dateFn = "Date(1971,3,8)";  
var myDate;  
eval("myDate = new " + dateFn + ";");  
  
document.write(myDate);  
  
// Output: Thu Apr 8 00:00:00 PDT 1971  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用されます**:[グローバル オブジェクト](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [String オブジェクト](../../javascript/reference/string-object-javascript.md)