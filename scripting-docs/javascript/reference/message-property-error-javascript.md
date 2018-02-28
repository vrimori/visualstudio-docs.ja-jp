---
title: "message プロパティ (Error) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- message
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Message property
ms.assetid: 8cab0392-e0db-4714-827c-47ab04e8b4f2
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9dbd2db6c6d31dc48d90c3b07d2388eacf73ae7a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="message-property-error-javascript"></a>message プロパティ (Error) (JavaScript)
エラー メッセージの文字列を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
errorObj.message  
```  
  
## <a name="parameters"></a>パラメーター  
 `errorObj`  
 必須です。 インスタンス`Error`オブジェクト。  
  
## <a name="remarks"></a>コメント  
 `message`プロパティを特定のエラーに関連付けられているエラー メッセージを含む文字列を返します。  
  
 `description`と`message`プロパティは、同じ機能を提供します。 `description`プロパティは下位互換性;`message`プロパティは、ECMA 規格に準拠しています。  
  
## <a name="example"></a>例  
 次の例では、TypeError をスローする例外が発生し、エラーおよびそのメッセージの名前を表示します。  
  
```JavaScript  
try  
{  
    // Cause an error.  
    var x = y;  
}  
catch(e)  
{  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
```  
  
## <a name="example"></a>例  
 このコードによる出力は次のとおりです。  
  
```JavaScript  
Error Message: 'y' is undefined  
Error Code: 5009  
Error Name: TypeError  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **適用されます**: [Error オブジェクト](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [description プロパティ (Error)](../../javascript/reference/description-property-error-javascript.md)   
 [name プロパティ (Error)](../../javascript/reference/name-property-error-javascript.md)