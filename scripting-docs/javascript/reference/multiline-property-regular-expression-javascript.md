---
title: "multiline プロパティ (Regular Expression) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: multiline
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: multiline property
ms.assetid: ca7b276a-1fe2-4189-ac27-f089ab3e9974
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 289cb8d8e103d8c4ac1b1ef06714105d21cba743
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="multiline-property-regular-expression-javascript"></a>multiline プロパティ (Regular Expression) (JavaScript)
Multiline フラグの状態を示すブール値を返します (**m**) 正規表現で使用します。 既定値は**false**です。 読み取り専用です。  
  
## <a name="syntax"></a>構文  
  
```  
  
rgExp.multiline  
```  
  
## <a name="remarks"></a>コメント  
 必要な`rgExp`引数がのインスタンスでは、`RegExp`オブジェクト  
  
 **複数行にわたる**プロパティから返される**true**かどうかする multiline フラグは、正規表現に設定されを返します**false**されていない場合。 **複数行にわたる**プロパティは**true**で正規表現オブジェクトが作成された場合、 **m**フラグ。  
  
 場合**複数行にわたる**は**false**、"^"、文字列の末尾位置を文字列であり、「$」の一致の先頭の位置に対応します。 場合**複数行にわたる**は**true**、"^""\n"または"\r"、「$」の直後の位置が、文字列の末尾と一致すると、"\n の前の位置も文字列の先頭位置に対応"または"\r"です。  
  
## <a name="example"></a>例  
 次の例の動作を示しています、**複数行にわたる**プロパティです。 "M"の関数に渡すと、次に示す、"while"という単語は語に置き換えられます。"と"です。 これは、複数行のフラグに設定されているためと、"while"という単語が改行文字の後に、行の先頭に発生します。 複数行のフラグは、複数行文字列で実行する検索を使用します。  
  
```JavaScript  
function RegExpMultilineDemo(flag){  
   // The flag parameter is a string that contains  
   // g, i, or m.  The flags can be combined.  
  
   // Check flags for validity.  
   if (flag.match(/[^gim]/))  
      {  
      return ("Flag specified is not valid");  
      }  
  
   // Create the string on which to perform the replacement.  
   var ss = "The man hit the ball with the bat ";  
   ss += "\nwhile the fielder caught the ball with the glove.";  
  
   // Replace "while" with "and".  
   var re = new RegExp("^while", flag);  
   var r = ss.replace(re, "and");          
  
   // Output the multiline flag and the resulting string.  
   var s = "";  
   s += "Result for multiline = " + re.multiline.toString();  
   s += ": " + r;  
  
   return(s);  
  
}  
  
sa = RegExpMultilineDemo("m");  
sb = RegExpMultilineDemo("");  
document.write (sa + "<br />" + sb);  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用されます**: [Regular Expression オブジェクト](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [global プロパティ (Regular Expression)](../../javascript/reference/global-property-regular-expression-javascript.md)   
 [ignoreCase プロパティ (Regular Expression)](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)   
 [正規表現の構文 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)