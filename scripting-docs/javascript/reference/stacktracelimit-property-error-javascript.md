---
title: stackTraceLimit プロパティ (Error) (JavaScript) |Microsoft ドキュメント
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
- Error.stackTraceLimit
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- error stack track limit [JavaScript]
- JavaScript error stack
- error stack [JavaScript]
- JavaScript stack trace limit
ms.assetid: 127ef8e8-892e-4263-9ebc-03364af01212
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9af736ee8b385f93b761f1dfa021c23ee5376292
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640572"
---
# <a name="stacktracelimit-property-error-javascript"></a>stackTraceLimit プロパティ (Error) (JavaScript)
取得または表示するエラーのフレームの数値と等価であるスタック トレース制限を設定します。 既定の制限は 10 です。  
  
## <a name="syntax"></a>構文  
  
```  
  
Error  
.stackTraceLimit   
```  
  
## <a name="remarks"></a>コメント  
 設定することができます、 `stackTraceLimit` 0、正の値にプロパティと`Infinity`です。 場合、`stackTraceLimit`プロパティが設定されて、エラーがスロー時に 0、スタック トレースに表示されません。 プロパティが負の値または数値以外の値に設定されている場合は、値が 0 に変換されます。 設定されている、stackTraceLimit 場合`Infinity`、スタック全体を表示します。 それ以外の場合、`ToUint32`を使用して、値を変換します。  
  
## <a name="example"></a>例  
 次の例では、設定およびスタック トレース制限を取得する方法を示します。  
  
```JavaScript  
try  
    {  
    var err = new Error("my error");  
    Error.stackTraceLimit = 7;  
    throw err;  
    }  
catch(e)  
    {  
    document.write ("Error stack trace limit: ")  
    document.write (Error.stackTraceLimit);  
    }  
```  
  
## <a name="requirements"></a>要件  
 Internet Explorer 10 でサポートされて[!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]アプリ。  
  
 **適用されます**: [Error オブジェクト](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [description プロパティ (Error)](../../javascript/reference/description-property-error-javascript.md)   
 [message プロパティ (Error)](../../javascript/reference/message-property-error-javascript.md)   
 [name プロパティ (Error)](../../javascript/reference/name-property-error-javascript.md)   
 [stack プロパティ (Error)](../../javascript/reference/stack-property-error-javascript.md)