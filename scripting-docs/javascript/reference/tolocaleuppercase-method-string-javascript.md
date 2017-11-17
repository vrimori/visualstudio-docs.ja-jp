---
title: "toLocaleUpperCase メソッド (String) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toLocaleUpperCase
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toLocaleUpperCase method
ms.assetid: e927adb6-475e-44b2-91f7-cedda10a39b0
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07a89560dde0319598da30fc3451524112b99eac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="tolocaleuppercase-method-string-javascript"></a>toLocaleUpperCase メソッド (String) (JavaScript)
すべてのアルファベット文字が大文字にアカウントのホストに変換後の環境の現在のロケールをされている文字列を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
stringVar.toLocaleUpperCase( )  
```  
  
## <a name="remarks"></a>コメント  
 必要な`stringVar`参照は、`String`オブジェクトまたは文字列リテラルです。  
  
 `toLocaleUpperCase`メソッドは、ホスト環境の現在のロケールを考慮に入れて、文字列の文字を変換します。 ほとんどの場合、結果は同じ結果として、`toUpperCase`メソッドです。 言語の規則が正規の Unicode の大文字小文字マップと競合する場合、結果が異なります。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用されます**:[文字列オブジェクト](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [toLocaleLowerCase メソッド (String)](../../javascript/reference/tolocalelowercase-method-string-javascript.md)   
 [toUpperCase メソッド (String)](../../javascript/reference/touppercase-method-string-javascript.md)