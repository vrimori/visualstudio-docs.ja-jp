---
title: toString メソッド (エラー) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d6d9712-c06d-4b31-9bc9-e46f6bb5cd38
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d774ff8c0f5338f4178b2262bf8ac8cadc074453
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640592"
---
# <a name="tostring-method-error"></a>toString メソッド (エラー)
エラーの文字列表現を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
error.toString()  
```  
  
## <a name="parameters"></a>パラメーター  
 `date`  
 必須です。 文字列として表現するエラーです。  
  
## <a name="return-value"></a>戻り値  
 返します。"エラー:"さらに、エラー メッセージ。  
  
## <a name="example"></a>例  
 次の例では、使用、`toString`エラーを持つメソッドです。  
  
```JavaScript  
var myError = new Error();  
myError.message = "My Error";  
var errorString = myError.toString();  
document.write(errorString);  
  
// Output: Error: My Error  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]