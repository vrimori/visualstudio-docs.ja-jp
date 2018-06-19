---
title: toLocaleLowerCase メソッド (String) (JavaScript) |Microsoft ドキュメント
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
- toLocaleLowerCase
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toLocaleLowerCase method
ms.assetid: add894d3-d14a-4dbc-a9b9-7ad1d3a2e581
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 642ced387e0d3b4cf763767ec147d6160ed7d36b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640472"
---
# <a name="tolocalelowercase-method-string-javascript"></a>toLocaleLowerCase メソッド (String) (JavaScript)
ホスト環境の現在のロケールを考慮に入れてをすべての英字を小文字に変換します。  
  
## <a name="syntax"></a>構文  
  
```  
  
stringVar.toLocaleLowerCase( )  
```  
  
## <a name="remarks"></a>コメント  
 必要な`stringVar`参照は、`String`オブジェクトまたは文字列リテラルです。  
  
 `toLocaleLowerCase`メソッドは、ホスト環境の現在のロケールを考慮に入れて、文字列の文字を変換します。 ほとんどの場合、結果は、同じの結果として、`toLowerCase`メソッドです。 言語の規則が正規の Unicode の大文字小文字マップと競合する場合、結果が異なります。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用されます**:[文字列オブジェクト](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [toLocaleUpperCase メソッド (String)](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)   
 [toLowerCase メソッド](../../javascript/reference/tolowercase-method-javascript.md)