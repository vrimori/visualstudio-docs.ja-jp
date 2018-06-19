---
title: description プロパティ (Error) (JavaScript) |Microsoft ドキュメント
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
- Description
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- error handling, error description
- Description property
- errors, description
ms.assetid: ea727f1e-2041-4400-965c-67e6d47a1ff0
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6135951fdf65698ed48b9bbacdcc55c1aac22d41
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636362"
---
# <a name="description-property-error-javascript"></a>description プロパティ (Error) (JavaScript)
特定のエラーと関連付けられたエラーを説明する文字列を設定するか、または返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object  
.description [= stringExpression]  
```  
  
## <a name="parameters"></a>パラメーター  
 *object*  
 必須です。 任意のインスタンス、`Error`オブジェクト。  
  
 `stringExpression`  
 省略可能です。 エラーの説明を含む文字列式です。  
  
## <a name="remarks"></a>コメント  
 **説明**プロパティには、特定のエラーに関連付けられているエラー メッセージ文字列が含まれています。 ユーザーは、エラーのアラートを生成するには、このプロパティに含まれている値を使用します。  
  
 **説明**と**メッセージ**プロパティは、同じ機能を提供;**説明**プロパティは下位互換性を提供; **メッセージ**プロパティは、ECMA 規格に準拠しています。  
  
## <a name="example"></a>例  
 次の例では、使用、**説明**プロパティです。  
  
```JavaScript  
try  
{  
// Cause an error:  
    x = y     
}  
catch(e)  
{  
// Prints "[object Error]":  
    document.write(e)  
    document.write (" ");  
// Prints 5009:  
    document.write((e.number & 0xFFFF))    
    document.write (" ");  
// Prints "'y' is undefined":  
    document.write(e.description);  
    document.write (" ");  
// Prints "'y' is undefined":  
    document.write(e.message)  
}  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **適用されます**: [Error オブジェクト](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [number プロパティ (Error)](../../javascript/reference/number-property-error-javascript.md)   
 [message プロパティ (Error)](../../javascript/reference/message-property-error-javascript.md)   
 [name プロパティ (Error)](../../javascript/reference/name-property-error-javascript.md)