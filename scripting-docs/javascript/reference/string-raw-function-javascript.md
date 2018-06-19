---
title: String.raw 関数 (JavaScript) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b1038b73-3944-4645-b075-3a674b313762
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 53df2bf0e455da8b1ccc6de3cbf3f4e3ebee4c09
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640162"
---
# <a name="stringraw-function-javascript"></a>String.raw 関数 (JavaScript)
テンプレート文字列の未加工の文字列形式を返します。  
  
## <a name="syntax"></a>構文  
  
```  
String.raw`templateStr`;  
String.raw(obj, ...substitutions);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `templateStr`  
 必須です。 テンプレート文字列。  
  
 `obj`  
 必須です。 { raw: 'value' }.などのオブジェクト リテラル表記を使用して指定された正しい形式のオブジェクト。  
  
 `...substitutions`  
 省略可能です。 配列 (、 [rest パラメーター](../../javascript/functions-javascript.md)) の 1 つ以上の置換値で構成されます。  
  
## <a name="remarks"></a>コメント  
 `String.raw`関数で使用される[テンプレート文字列](../../javascript/advanced/template-strings-javascript.md)です。 未加工の文字列には、文字列内に存在するすべてのエスケープ文字と円記号が含まれます。  
  
 `obj` が正しい形式のオブジェクトではない場合には、エラーがスローされます。  
  
## <a name="example"></a>例  
  
```  
function log(arg) {  
    if(console && console.log) {  
        console.log(arg);  
    }  
};  
  
var name = "bob";  
  
log(`hello \t${name}`);  
log(String.raw`hello \t${name}`);  
// The following usage for String.raw is supported but  
// is not typical.  
log(String.raw({ raw: 'fred'}, 'F', 'R', 'E'));  
  
// Output:  
// hello   bob  
// hello \tbob  
// fFrReEd   
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]