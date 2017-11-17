---
title: "コメント ステートメント (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Comment_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- comments, ignoring
- comment statements
ms.assetid: b604824f-ac17-49d3-bcdb-2a893ab5fff8
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c270379725550e116928bbecd69e6be51c34992f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="comment-statements-javascript"></a>コメント ステートメント (JavaScript)
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] パーサーがコメントを無視するようにします。  
  
## <a name="syntax"></a>構文  
  
```  
Single-line Comment:  
// comment   
```  
  
```  
Multiline Comment:  
/*  
comment  
*/  
```  
  
```  
Comments with conditional compilation:  
//@CondStatement   
  
/*@  
condStatement  
@*/  
```  
  
## <a name="remarks"></a>コメント  
 `comment` 引数は、スクリプトに含めるコメントのテキストです。 `condStatement` 引数は、条件付きコンパイルがアクティブになっている場合に使用します。 単一行コメントを使用する場合は、"//" と "@" 文字の間にスペースを入れないでください。  
  
 コメントを使用して、スクリプトの一部が [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] パーサーに読み取られないようにします。 コメントを使用して、プログラム内に説明のための注記を含めることができます。  
  
 単一行コメントを使用する場合、パーサーは、コメント マーカーと行末の間にあるすべてのテキストを無視します。 複数行コメントを使用する場合、パーサーは、開始マーカーと終了マーカーの間にあるすべてのテキストを無視します。  
  
 コメントを使用して、条件付きコンパイルをサポートすると共に、その機能をサポートしないブラウザーとの互換性も維持することができます。 これらのブラウザーは、それらの形式のコメントを、それぞれ単一行または複数行のコメントとして処理します。  
  
## <a name="example"></a>例  
 次の例では、コメントの最も一般的な使用方法を示します。  
  
```JavaScript  
/* This is a multiline comment that  
    can span as many lines as necessary.  */  
function myfunction(arg1, arg2){  
    var r;  
    // This is a single line comment.  
    r = arg1 + arg2  
    return(r);  
}  
```  
  
## <a name="example"></a>例  
 次の例では、条件付きコンパイルを使用する方法を示します。 この例では、`@cc_on` ステートメントによって条件付きコンパイルがアクティブにされた場合にだけ使用される、特殊なコメント区切り文字を使用しています。 条件付きコンパイルをサポートしないスクリプト エンジンでは、条件付きコンパイルがサポートされていないというメッセージのみが表示されます。  
  
```JavaScript  
/*@cc_on @*/  
/*@if (@_jscript_version >= 4)  
    alert("JavaScript version 4 or better");  
    @else @*/  
    alert("Conditional compilation not supported by this scripting engine.");  
/*@end @*/  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]