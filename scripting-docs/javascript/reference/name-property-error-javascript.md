---
title: "name プロパティ (Error) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: name
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Name property
- name property, error name
ms.assetid: 94df2d6b-f1a1-4931-a956-0a930cb87f76
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1a12157b4c467499fab23f7c4cb1be91e9ac5440
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="name-property-error-javascript"></a>name プロパティ (Error) (JavaScript)
エラー名を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
errorObj.  
name  
  
```  
  
## <a name="parameters"></a>パラメーター  
 `errorObj`  
 必須です。 インスタンス`Error`オブジェクト。  
  
## <a name="remarks"></a>コメント  
 **名前**プロパティは、エラーの名前または例外の種類を返します。 ランタイム エラーが発生したときに、name プロパティは、ネイティブの例外の種類は次のいずれかに設定します。  
  
|例外の種類|説明|  
|--------------------|-------------|  
|ConversionError|このエラーは、オブジェクトを変換できないものに変換が試行されるたびに発生します。|  
|RangeError|このエラーは、引数が、許容範囲を超えている関数に渡されたときに発生します。 構築しようとする場合、たとえば、このエラーが発生、`Array`有効な正の整数ではない長さのオブジェクト。|  
|ReferenceError|このエラーは、無効な参照が検出されたときに発生します。 このエラーが発生、たとえば、予期した参照が`null`です。|  
|RegExpError|このエラーは、正規表現でコンパイル エラーが発生したときに発生します。 正規表現をコンパイルした場合、ただし、このエラーが発生することはできません。 このエラーが発生、たとえば、正規表現が無効な構文またはフラグを以外のパターンで宣言されているときに**すれば**、 **g**、または**m**が含まれている場合、または2 回以上同じフラグです。|  
|SyntaxError|このエラーは、ソース テキストは解析され、そのソース テキストが正しい構文に従っていないときに発生します。 このエラーが発生などの場合、`eval`有効なプログラム テキストではない引数を持つ関数が呼び出されます。|  
|TypeError|このエラーは、オペランドの実際の型に必要な型が一致しないときに発生します。 このエラーが発生した場合の例は、関数呼び出しのものに対して行われたオブジェクトではないか、呼び出しをサポートしていないことです。|  
|URIError|このエラーは、無効な Uniform Resource Indicator (URI) が検出されたときに発生します。 たとえば、これは、エラー エンコードまたはデコード対象の文字列内に無効な文字が見つかったときに発生します。|  
  
## <a name="example"></a>例  
 次の例では、TypeError をスローする例外が発生し、エラーおよびそのメッセージの名前を表示します。  
  
```JavaScript  
try  
{  
    var x = y;  
}  
catch(e)  
{  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
```  
  
## <a name="example"></a>例  
 このコードによる出力は次のとおりです。  
  
```JavaScript  
Error Message: 'y' is undefined  
Error Code: 5009  
Error Name: TypeError  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用されます**: [Error オブジェクト](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [description プロパティ (Error)](../../javascript/reference/description-property-error-javascript.md)   
 [message プロパティ (Error)](../../javascript/reference/message-property-error-javascript.md)   
 [number プロパティ (Error)](../../javascript/reference/number-property-error-javascript.md)