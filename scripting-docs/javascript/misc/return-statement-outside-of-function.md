---
title: '&#39;以外の場合は戻り値 &#39;関数の外側でステートメント |Microsoft ドキュメント'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07b633c87dc11b291a5a5783f8121b2a368996d6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633512"
---
# <a name="39return39-statement-outside-of-function"></a>&#39;以外の場合は戻り値 &#39;関数の外側でステートメント
使用する、`return`グローバル スコープで、コードのステートメント。 `return`ステートメントが関数の本体内でのみ表示されます。  
  
 持つ関数を呼び出して、`()`演算子は式です。 すべての式の値であります。`return`関数によって返される値を指定するステートメントを使用します。 一般的な形式は次のとおりです。  
  
```  
  
return [ expression ];  
```  
  
 ときに、`return`ステートメントを実行すると、*式*が評価され、関数の値として返されます。 式がない場合は**未定義**が返されます。  
  
 関数の実行を停止するときに、`return`関数本体に残っているその他のステートメントがある場合でも、ステートメントを実行します。 この規則の例外は場合、**返す**ステートメント内で発生、**を再試行してください**ブロックでは、対応する**最後に**、コードのブロック、 **最後に**ブロックは、関数が返す前に実行されます。  
  
 実行することがなく、関数本体の末尾に達するために、関数が返す場合、`return`ステートメントでは、返される値は、**未定義**値 (つまり、関数の結果より大きな式の一部として使用できません).  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   削除、 `return` (グローバル スコープ)、コードの本体からのステートメント。  
  
## <a name="see-also"></a>関連項目  
 [return ステートメント](../../javascript/reference/return-statement-javascript.md)   
 [Function オブジェクト](../../javascript/reference/function-object-javascript.md)   
 [caller プロパティ (Function)](../../javascript/reference/caller-property-function-javascript.md)