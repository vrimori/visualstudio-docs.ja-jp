---
title: lastIndex プロパティ (RegExp) (JavaScript) |Microsoft ドキュメント
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
- lastIndex
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- lastIndex property
ms.assetid: c8ae2a13-6dff-4cbe-b662-aca3d66c2a7f
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d5e24fe14d335e1494b13518543f56025625de0b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637812"
---
# <a name="lastindex-property-regexp-javascript"></a>lastIndex プロパティ (RegExp) (JavaScript)
検索した文字列では、次の一致の開始文字位置を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
RegExp.lastIndex  
```  
  
## <a name="remarks"></a>コメント  
 このプロパティに関連付けられているオブジェクトは、常にグローバル`RegExp`オブジェクト。  
  
 `lastIndex`プロパティが 0 から始まる場合、その最初の文字のインデックスは 0 です。 その初期値は-1 です。 その値が変更されるは、一致が加えられるたびにします。  
  
 `lastIndex`によってプロパティが変更された、`exec`と**テスト**のメソッド、`RegExp`オブジェクト、および`match`、**置換**、および**を分割**のメソッド、`String`オブジェクト。  
  
 値に、次の規則が適用される`lastIndex`:  
  
-   一致が存在しない場合`lastIndex`が-1 に設定します。  
  
-   場合`lastIndex`が、文字列の長さより大きい**テスト**と`exec`失敗および`lastIndex`が-1 に設定します。  
  
-   場合`lastIndex`が正規表現の一致パターンが空の文字列と一致する場合、文字列の長さと等しい。 それ以外の場合、照合は失敗し、`lastIndex`が-1 にリセットします。  
  
-   それ以外の場合、`lastIndex`が一致する最後の直後の位置に設定します。  
  
## <a name="example"></a>例  
 次の例では、使用、`lastIndex`プロパティです。 この関数は、検索文字列を反復処理し、出力、**インデックス**と`lastIndex`文字列内の各単語の値。  
  
```JavaScript  
function RegExpTest()  
{  
   var ver = Number(ScriptEngineMajorVersion() + "." + ScriptEngineMinorVersion())  
   if (ver < 5.5)  
   {  
      document.write("You need a newer version of JavaScript for this to work");  
      return;  
   }  
  
   var src = "The quick brown fox jumps over the lazy dog.";  
  
   // Create regular expression pattern with a global flag.  
   var re = /\w+/g;  
  
   // Get the next word, starting at the position of lastindex.  
   var arr;  
   while ((arr = re.exec(src)) != null)  
      {  
      // New line:  
      document.write ("<br />");    
      document.write (arr.index + "-" + re.lastIndex + " ");  
      document.write (arr);  
      }  
}  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用されます**: [RegExp オブジェクト](../../javascript/reference/regexp-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [正規表現の構文 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)