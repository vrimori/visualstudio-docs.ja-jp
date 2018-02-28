---
title: "new 演算子 (JavaScript) |Microsoft ドキュメント"
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
- new_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- new operator in JavaScript
ms.assetid: 5ea556ba-7ae6-426c-8430-9032eee5a0a5
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ad004abb534d69bed1a1bd9bbd2ae96755544b9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="new-operator-javascript"></a>new 演算子 (JavaScript)
新しいオブジェクトを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
new constructor ([arguments])   
```  
  
## <a name="parameters"></a>パラメーター  
 `constructor`  
 必須です。 オブジェクトのコンス トラクターです。 コンス トラクターに引数がない場合、かっこを省略できます。  
  
 `arguments`  
 省略可能です。 新しいオブジェクトのコンス トラクターに渡される引数。  
  
## <a name="remarks"></a>コメント  
 `new`演算子は、次のタスクを実行します。  
  
-   メンバーを持たないオブジェクトを作成します。  
  
-   ポインターとして新しく作成されたオブジェクトを渡して、そのオブジェクトのコンス トラクターを呼び出します、`this`ポインター。  
  
-   コンス トラクターは、コンス トラクターに渡される引数に基づいてオブジェクトを初期化します。  
  
 これらは、の有効な使用例については、**新しい**演算子。  
  
```JavaScript  
my_object = new Object;  
my_array = new Array();  
my_date = new Date("Jan 5 1996");  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [function ステートメント](../../javascript/reference/function-statement-javascript.md)