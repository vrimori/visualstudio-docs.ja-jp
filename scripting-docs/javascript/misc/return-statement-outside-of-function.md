---
title: 'return' ステートメントが関数の外にあります  |Microsoft Docs'
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
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49846519"
---
# <a name="39return39-statement-outside-of-function"></a>'return' ステートメントが関数の外にあります
使用した、`return`コードのグローバル スコープ内のステートメント。 `return`ステートメントは、関数の本体でのみ表示する必要があります。  
  
 持つ関数を呼び出す、`()`演算子は、式です。 すべての式の値であります。`return`関数によって返される値を指定するステートメントを使用します。 一般的な形式です。  
  
```  
  
return [ expression ];  
```  
  
 ときに、`return`ステートメントを実行すると、*式*が評価され、関数の値として返されます。 式がない場合**未定義**が返されます。  
  
 関数の実行を停止するときに、`return`関数本体に残っている他のステートメントがある場合でも、ステートメントを実行します。 このルールの例外は場合、**返す**ステートメント内で発生、**お試しください**ブロックは、対応する**最後に**ブロック、コード、 **最後に**ブロックは、関数が戻る前に実行されます。  
  
 実行することがなく、関数本体の末尾に達したため、関数が返す場合、`return`ステートメントで返される値が、**未定義**値 (つまり、関数の結果より大きな式の一部として使用できません).  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   削除、 `return` (グローバル スコープ)、コードのメイン本体ステートメント。  
  
## <a name="see-also"></a>関連項目  
 [return ステートメント](../../javascript/reference/return-statement-javascript.md)   
 [関数オブジェクト](../../javascript/reference/function-object-javascript.md)   
 [caller プロパティ (Function)](../../javascript/reference/caller-property-function-javascript.md)
