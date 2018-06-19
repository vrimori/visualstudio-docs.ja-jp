---
title: 比較演算子 (JavaScript) |Microsoft ドキュメント
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
- Comparison
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- comparison operators, script
- greater than operator
- comparison operators
- greater than or equal to operator
- inequity operator
- identity operator
ms.assetid: 084f90f0-d010-47cf-96dd-13d637fc9b68
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 067d570523fc2241b4f2e0442785a49aedb15200
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634202"
---
# <a name="comparison-operators-javascript"></a>比較演算子 (JavaScript)
比較の結果を示すブール値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
expression1 comparisonoperator expression2  
```  
  
## <a name="parameters"></a>パラメーター  
 `expression1`  
 任意の式。  
  
 `comparisonoperator`  
 任意の比較演算子です。  
  
 `expression2`  
 任意の式。  
  
## <a name="remarks"></a>コメント  
 文字列を比較するときに[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]文字列式の Unicode 文字の値を使用します。  
  
 演算子の異なるグループの型との値に応じて動作方法を以下に示します`expression1`と`expression2`:  
  
 関係演算子: `<`、 `>`、 `<=`、`>=`  
  
-   両方の変換を試みる`expression1`と`expression2`数値にします。  
  
-   両方の式が文字列である場合は、文字列比較を行います。  
  
-   いずれかの式が場合`NaN`、return`false`です。  
  
-   正のゼロを負のゼロに等しくなります。  
  
-   負の無限大では、それ自体を含むすべての式より小さいです。  
  
-   正の無限大では、それ自体を含むすべてのものを超えています。  
  
 等値演算子: `==`、`!=`  
  
-   2 つの式の型が異なる場合は、文字列、数値、またはブール値に変換するしようとします。  
  
-   `NaN`それ自体を含むものに等しくありません。  
  
-   正のゼロを負のゼロに等しくなります。  
  
-   `null`両方に等しい`null`と`undefined`です。  
  
-   値の場合に同じ文字列、等価な数値で、同じオブジェクト、同一のブール値は等しいと見なされますまたは (場合さまざまな種類) をこのような状況の 1 つに強制変換することができます。  
  
-   その他のすべての比較は、等しくないと見なされます。  
  
 Id オペレーター: `===`、`!==`  
  
 これらの演算子は型変換は行われませんする点を除いて、等値演算子と同じ動作をします。 かどうか、型の両方の式が同じでないこれらの式はその常に返す`false`です。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)