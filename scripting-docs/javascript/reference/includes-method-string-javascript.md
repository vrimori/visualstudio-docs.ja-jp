---
title: "includes メソッド (String) (JavaScript) |Microsoft ドキュメント"
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
ms.assetid: 2639e4e5-23ba-424a-80ea-be067a4cd65e
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 848143b64d3e32452aea41f08b6f5c57879d3e17
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="includes-method-string-javascript"></a>includes メソッド (String) (JavaScript)
渡された文字列が文字列オブジェクトに含まれているかどうかを示すブール値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
stringObj.includes(substring [, position]);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `stringObj`  
 必須です。 テスト対象の String オブジェクト。  
  
 `substring`  
 必須です。 テストする文字列。  
  
 `position`  
 省略可能です。 文字列オブジェクトに存在するかテストする、最初の文字の位置です (0 から始まります)。  
  
## <a name="return-value"></a>戻り値  
 渡された文字列が文字列オブジェクトに含まれる場合、`includes` メソッドは `true` を返します。それ以外の場合は、`false` を返します。  
  
## <a name="remarks"></a>コメント  
  
## <a name="example"></a>例  
  
```JavaScript  
// Returns true   
"abcde".includes("cd")  
"abcde".includes("cd", 2)  
  
// Returns false  
"abcde".includes("CD")  
"abcde".includes("cd", 3)  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]