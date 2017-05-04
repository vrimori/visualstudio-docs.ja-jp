---
title: "演算子の優先順位 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "演算子の優先順位"
  - "優先順位"
ms.assetid: cf3c510a-2214-4b47-b8fe-3521298efaab
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# 演算子の優先順位 (JavaScript)
演算子の優先順位は、式を評価する際の演算子の実行順序を説明します。  優先順位の高い演算は、優先順位の低い演算より先に実行されます。  たとえば、乗算は加算より先に実行されます。  
  
## [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] の演算子  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] の演算子を優先順位の高い順に上から並べた表を次に示します。  同じ優先順位の演算子は、左から右に評価されます。  
  
|演算子|説明|  
|---------|--------|  
|.\[ \] \( \)|フィールド アクセス、配列のインデックス付け、関数の呼び出し、および式のグループ化|  
|\+\+ \-\- \- ~ \! delete new typeof void|単項演算子、戻り値の型、オブジェクトの作成、未定義の値|  
|\* \/ %|乗算、除算、剰余|  
|\+ \- \+|加算、減算、文字列の連結|  
|\<\< \>\> \>\>\>|ビット シフト|  
|\< \<\= \> \>\= instanceof|小なり、以下、大なり、以上、instanceof|  
|\=\= \!\= \=\=\= \!\=\=|等値、非等値、厳密等価、厳密非等価|  
|&|ビットごとの AND|  
|^|ビットごとの XOR|  
|&#124;|ビットごとの OR|  
|&&|論理 AND|  
|&#124;&#124;|論理 OR|  
|?:|条件|  
|\= *OP*\=|代入、演算して代入 \(\+\=、&\= など\)|  
|,|複数の評価|  
  
 かっこは、演算子の優先順位で決定される評価の順序を変更するために使用します。  つまり、かっこの内側の演算は、かっこの外側の演算よりも先に実行されます。ただし、かっこの内側の演算子には通常の優先順位が適用されます。  
  
 たとえば、次のようになります。  
  
```javascript  
var result = 78 * 96 + 3;  
document.write(result);  
document.write("<br/>");  
  
result = 78 * (9 + 3);  
document.write(result);  
  
// Output:  
// 7491  
// 936  
```  
  
 最初の式には、\=、\*、および \+ の 3 つの演算子があります。  演算の優先順位の規則に従うと、これらの演算子は \*、\+、\= の順に実行されます \(78 \* 96 \= 7488、7488 \+ 3 \= 7491\)。  
  
 2 番目の式では、\( \) 演算子が最初に評価されるため、加算式が乗算の前に評価されます \(9 \+ 3 \= 12、12 \* 78 \= 936\)。  
  
 次の例は、さまざまな演算子が含まれ `true` に解決される式を示しています。  
  
```javascript  
var num = 10;  
  
if(5 == num / 2 && (2 + 2 * num).toString() === "22") {  
    document.write(true);  
}  
    // Output:  
    // true  
```  
  
 演算子は、グループ化するための \( \)、\*、グループ内の \+、関数の "."、関数の \( \)、\/、\=\=、\=\=\=、&& の順に評価されます。