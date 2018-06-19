---
title: stack プロパティ (Error) (JavaScript) |Microsoft ドキュメント
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
- Error.stack
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- JavaScript error stack
- error stack [JavaScript]
ms.assetid: 1dc21fdd-853c-4664-bf1c-24eb1f6f2daf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14e4a2537b1543b7e8d9727afdeb8ea5dee61bbc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641142"
---
# <a name="stack-property-error-javascript"></a>stack プロパティ (Error) (JavaScript)
スタック トレース フレームを含む文字列としてエラー スタックを取得または設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object  
.stack   
```  
  
## <a name="remarks"></a>コメント  
 エラーが構築され、エラーが発生してトレース情報が取得されると、`stack` プロパティは、`undefined` に設定されます。 エラーが複数回発生すると、エラーが発生するたびに `stack`プロパティが更新されます。  
  
 スタック フレームは、次の形式で表示されます: **FunctionName で (\<完全修飾名または URL >:\<行番号 >:\<列番号 >)**  
  
 独自のエラー オブジェクトを作成し、値にスタック トレースを設定すると、エラーがスローされたときに、値は上書きされません。  
  
 `stack` プロパティの場合、フレーム内にインライン関数は表示されません。 物理スタックのみが表示されます。  
  
## <a name="example"></a>例  
 次の例では、エラーをキャッチしたときにスタックを取得する方法を示します。  
  
```JavaScript  
try  
    {  
        var x = y.name;  
    }  
catch(e)  
    {  
        document.write ("Error stack: ")  
        document.write (e.stack);  
    }  
```  
  
## <a name="example"></a>例  
 次の例では、スタックを設定してから取得する方法を示します。  
  
```JavaScript  
try  
    {  
        var err = Error("my error");  
        err.stack = "my stack trace";  
        throw err;  
    }  
catch(e)  
    {  
        document.write ("Error stack: ")  
        document.write (e.stack);  
    }  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]  
  
 **適用されます**: [Error オブジェクト](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [description プロパティ (Error)](../../javascript/reference/description-property-error-javascript.md)   
 [message プロパティ (Error)](../../javascript/reference/message-property-error-javascript.md)   
 [name プロパティ (Error)](../../javascript/reference/name-property-error-javascript.md)   
 [stackTraceLimit プロパティ (Error)](../../javascript/reference/stacktracelimit-property-error-javascript.md)