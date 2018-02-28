---
title: "switch ステートメント (JavaScript) |Microsoft ドキュメント"
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
- switch_JavaScriptKeyword
- default_JavaScriptKeyword
- case_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- switch statement
ms.assetid: 61f80e8b-3739-4146-a893-c2832d92b28c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a301fc8bcc72b48c6ba8e999c0ebb70fe9d92b41
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="switch-statement-javascript"></a>switch ステートメント (JavaScript)
指定した式の値がラベルと一致したときに 1 つ以上のステートメントを実行する機能を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
switch (expression) {  
    case label :  
        statementlist  
    case label :  
    default :  
        statementlist  
}   
```  
  
## <a name="parameters"></a>パラメーター  
 `expression`  
 評価される式。  
  
 `label`  
 識別子と照合する`expression`です。 場合`label`は、 `expression`、実行が始まる、 `statementlist` 、コロンの後すぐにし、いずれかを検出するまで、`break`ステートメントでは、これは省略可能なまたは末尾の`switch`ステートメントです。  
  
 `statementlist`  
 実行する 1 つ以上のステートメントを指定します。  
  
## <a name="remarks"></a>コメント  
 使用して、`default`句なしのラベルの値の一致する場合に実行されるステートメントの提供を`expression`です。 任意の場所内で使用できます、`switch`コード ブロック。  
  
 0 個以上`label`ブロックを指定することがあります。 ない場合は`label`の値に一致`expression`、および`default`ケースが指定されていない、ステートメントは実行されません。  
  
 実行を経由して流れます、`switch`次のようにステートメント。  
  
-   評価`expression`を見ます`label`一致が見つかるまでの順序で。  
  
-   場合、 `label` equals を値`expression`、それに付随する実行`statementlist`です。  
  
     までの実行を継続、`break`ステートメントが検出された、または`switch`ステートメントが終了します。 つまり、その複数`label`ブロックが実行された場合、`break`ステートメントは使用されません。  
  
-   ない場合は`label`equals`expression`に移動して、`default`ケース。 ある場合ありません`default`場合は、最後の手順に進みます。  
  
-   末尾の次のステートメントの実行を継続して、`switch`コード ブロック。  
  
## <a name="example"></a>例  
 次の例では、その型のオブジェクトをテストします。  
  
```JavaScript  
function MyObjectType(obj) {  
    switch (obj.constructor) {  
        case Date:  
            document.write("Object is a Date.");  
            break;  
        case Number:  
            document.write("Object is a Number.");  
            break;  
        case String:  
            document.write("Object is a String.");  
            break;  
        default:  
            document.write("Object is unknown.");  
    }  
}  
  
// Output when obj is a Date:  
// Object is a Date.  
  
// Output when obj is a Number:  
// Object is a Number.  
  
// Output when obj is a String:  
// Object is a String.  
  
// Output when obj is something other than a Date, Number, or String:  
// Object is unknown.  
  
```  
  
## <a name="example"></a>例  
 次のコードを使用しない場合は、`break`ステートメントです。  
  
```JavaScript  
function MyObjectType(obj) {  
    switch (obj.constructor) {  
        case Date:  
            document.write("Object is a Date.");  
        case Number:  
            document.write("Object is a Number.");  
        case String:  
            document.write("Object is a String.");  
        default:  
            document.write("Object is unknown.");  
    }  
}  
  
// Output when obj is a Date:  
// Object is a Date.Object is a Number.Object is a String.Object is unknown.  
  
// Output when obj is a Number:  
// Object is a Number.Object is a String.Object is unknown.  
  
// Output when obj is a String:  
// Object is a String.Object is unknown.  
  
// Output when obj is something other than a Date, Number, or String:  
// Object is unknown.  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [break ステートメント](../../javascript/reference/break-statement-javascript.md)   
 [if...else ステートメント](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)