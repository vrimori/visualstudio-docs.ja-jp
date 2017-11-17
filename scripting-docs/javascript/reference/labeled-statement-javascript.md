---
title: "ラベル付きステートメント (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: labeled_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- continue statement
- labeled statement
- identifiers, statements
ms.assetid: 019f898e-9e27-4be4-a22f-c5927c7fcae2
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd72b15d3fc9083ca127a48981c0cd0a7ee56b6c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="labeled-statement-javascript"></a>ラベル付きステートメント (JavaScript)
ステートメントの識別子を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
      label :  
   statements   
```  
  
## <a name="parameters"></a>パラメーター  
 *ラベル*  
 必須です。 ラベル付きステートメントを参照するときに使用される一意の識別子。  
  
 `statements`  
 省略可能です。 1 つまたは複数のステートメントに関連付けられている*ラベル*です。  
  
## <a name="remarks"></a>コメント  
 ラベルがによって使用される、**改**と**続行**するステートメントを指定するステートメント、**改**と**続行**を適用します。  
  
## <a name="example"></a>例  
 次のコードで、**続行**ステートメントを参照して、**の**前がループ、`Inner:`ステートメントです。 ときに`j`、24、**続行**ステートメントを**の**ループを使用して、次のイテレーションに移動します。 行ごとに 21 ~ 23 および 25 ~ 30 の数字を印刷します。  
  
```JavaScript  
Outer:  
for (i = 1; i <= 10; i++) {  
   document.write ("<br />");  
   document.write ("i: " + i);  
   document.write (" j: ");  
  
Inner:  
   for (j = 21; j <= 30; j++) {  
      if (j == 24)  
          {  
          continue Inner;  
      }  
      document.write (j + " ");  
  }  
}  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [break ステートメント](../../javascript/reference/break-statement-javascript.md)   
 [continue ステートメント](../../javascript/reference/continue-statement-javascript.md)