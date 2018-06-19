---
title: number プロパティ (Error) (JavaScript) |Microsoft ドキュメント
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
- Number
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Number property
ms.assetid: 8697e20b-a2b0-4e26-85c0-ab07ddfe8281
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bbc229e7d0572e1a3dbed056b344da7ff9ce7292
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639102"
---
# <a name="number-property-error-javascript"></a>number プロパティ (Error) (JavaScript)
特定のエラーと関連付けられた数値を設定したり、この数値を取得したりします。 `Error`オブジェクトの既定のプロパティは**数**です。  
  
## <a name="syntax"></a>構文  
  
```  
  
object  
.number [= errorNumber]  
```  
  
## <a name="parameters"></a>パラメーター  
 *オブジェクト*  
 任意のインスタンス、`Error`オブジェクト。  
  
 *エラー番号*  
 エラーを表す整数。  
  
## <a name="remarks"></a>コメント  
 エラー番号は 32 ビット値です。 上位 16 ビット ワードは機能コードで、下位のワードはエラー コードです。 エラー コードを調べるを使用して、 `&` (ビットごとと) と 16 進数の数値プロパティを結合する演算子`0xFFFF`です。  
  
## <a name="example"></a>例  
 次の例がスローされる例外が発生し、エラーの数から派生したエラー コードが表示されます。  
  
```JavaScript  
try  
    {  
    // Cause an error.  
    var x = y;  
    }  
catch(e)  
    {  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
  
    document.write ("Facility Code: ")  
    document.write(e.number>>16 & 0x1FFF)  
    document.write ("<br />");  
  
    document.write ("Error Message: ")  
    document.write (e.message)  
    }  
```  
  
## <a name="example"></a>例  
 このコードによる出力は次のとおりです。  
  
```JavaScript  
Error Code: 5009  
Facility Code: 10  
Error Message: 'y' is undefined  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **適用されます**: [Error オブジェクト](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [description プロパティ (Error)](../../javascript/reference/description-property-error-javascript.md)   
 [message プロパティ (Error)](../../javascript/reference/message-property-error-javascript.md)   
 [name プロパティ (Error)](../../javascript/reference/name-property-error-javascript.md)