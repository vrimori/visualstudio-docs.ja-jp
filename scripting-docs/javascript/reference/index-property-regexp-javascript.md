---
title: index プロパティ (RegExp) (JavaScript) |Microsoft ドキュメント
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
- index
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Index property
- matching strings
ms.assetid: d8be1ef6-1bf2-43cd-b0b5-567a61eabaad
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c6b11a5caf6e727b4d525b9a2d51eddd4542bc4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637362"
---
# <a name="index-property-regexp-javascript"></a>index プロパティ (RegExp) (JavaScript)
検索文字列と一致する最初の文字について、対象文字列内の先頭からの位置を返します。 読み取り専用です。  
  
## <a name="syntax"></a>構文  
  
```  
  
RegExp.index   
```  
  
## <a name="remarks"></a>コメント  
 このプロパティに関連付けられているオブジェクトは、常にグローバル`RegExp`オブジェクト。  
  
 **インデックス**プロパティは 0 から始まる。 初期値、**インデックス**プロパティは-1。 正常に実行するたびに値が変化します。  
  
## <a name="example"></a>例  
 次の例では、使用、**インデックス**プロパティです。 この関数は、検索文字列を反復処理し、出力、**インデックス**と`lastIndex`文字列内の各単語の値。  
  
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
      document.write (arr.index + "-" + arr.lastIndex + " ");  
      document.write (arr);  
      }  
}  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用されます**: [RegExp オブジェクト](../../javascript/reference/regexp-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [正規表現の構文 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)