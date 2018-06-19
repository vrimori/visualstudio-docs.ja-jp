---
title: valueOf メソッド (エラー) |Microsoft ドキュメント
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
ms.assetid: ca25c57d-c9ad-445b-8235-561390de680c
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c7593937530469142265f8081bf3472fa4935aee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640202"
---
# <a name="valueof-method-error"></a>valueOf メソッド (エラー)
エラーの文字列値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
error.valueOf()  
```  
  
#### <a name="parameters"></a>パラメーター  
 `error`オブジェクトがエラーの任意のインスタンス。  
  
## <a name="return-value"></a>戻り値  
 文字列"エラー:"さらに、エラー メッセージ。  
  
## <a name="example"></a>例  
 次の例では、使用、`valueOF`日付を持つメソッドです。  
  
```JavaScript  
var myError = new Error();  
myError.message = "This is an error.";  
var value = myError.valueOf();  
document.write(value);  
  
// Output: Error: This is an error.  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]