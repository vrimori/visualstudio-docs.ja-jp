---
title: "データのコピー、受け渡し、および比較 (JavaScript) | Microsoft Docs"
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
  - "配列 [Visual Studio], コピー (データを)"
  - "配列 [Visual Studio], 渡す (値を)"
  - "配列 [Visual Studio], 設定 (データ型を)"
  - "ByRef 引数"
  - "ByVal 引数"
  - "関数パラメーター"
  - "関数パラメーター, 関数パラメーターの概要"
  - "文字列比較"
  - "文字列比較, テスト (データの)"
ms.assetid: fbccd877-7249-45d4-bd9f-6bcd8ba94a6b
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# データのコピー、受け渡し、および比較 (JavaScript)
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] では、データの処理方法はデータ型に依存します。  
  
## 値渡しと参照渡し  
 数値およびブール値 \(**true** と **false**\) は、"値渡し" でコピー、受け渡し、および比較が実行されます。  値渡しで値をコピーまたは渡す場合、コンピューターのメモリ領域を割り当てて元の値をコピーします。  元の値を変更しても、元の値とコピーされた値は個別の要素であるため、コピーされた値に影響はありません \(逆の場合も同様です\)。  
  
 オブジェクト、配列、および関数は、"参照渡し" でコピー、受け渡し、および比較が行われます。  参照渡しで値をコピーまたは渡す場合、基本的に元の項目へのポインターを作成し、そのポインターをコピーされた値として使用します。  元の項目を変更すると、元の項目とコピーされた項目の両方が変更されます \(逆の場合も同様です\)。  実際に存在する項目は 1 つだけであり、"コピーされた項目" は実際にはコピーではなく、元のデータへのもう 1 つの参照です。  
  
 参照渡しの比較で結果が等しいと評価されるには、2 つの変数が同じ項目を参照している必要があります。  たとえば、2 つの異なる **Array** オブジェクトは、まったく同じ要素を持っていても、比較においては常に等しくないものとして識別されます。  比較処理を正しく行うには、一方の変数がもう一方の変数の参照である必要があります。  2 つの Array オブジェクトが同じ要素を持つかどうかを確認するには、**toString\(\)** メソッドの結果を比較します。  
  
 最後に、文字列は参照渡しで値をコピーまたは渡されますが、値渡しで比較されます。  2 つの **String** オブジェクトがある場合は \(**new** String\("something"\) を使用して作成\)、参照渡しで比較されますが、一方または両方の値が文字列値の場合は値渡しで比較されます。  
  
> [!NOTE]
>  ASCII 文字セットと ANSI 文字セットの構成の方法により、文字の順序で大文字は小文字より前になります。  たとえば、"Zoo" は "aardvark" より小さいと評価されます。大文字と小文字を区別しない一致検証を行うには、双方の文字列で **toUpperCase\(\)** または **toLowerCase\(\)** を呼び出します。  
  
## パラメーターを関数に渡す  
 関数に値渡しでパラメーターを渡す場合は、そのパラメーターの新しいコピーが作成されます。作成されたコピーは、その関数の中だけで存在します。  オブジェクトや配列は参照によって渡されますが、関数内の新しい値で直接上書きする場合、関数の外ではこの新しい値は反映されません。  関数の外でも有効なのは、オブジェクトのプロパティや配列の要素に対する変更だけです。  
  
 例 \(Internet Explorer のオブジェクト モデルを使用\):  
  
```javascript  
// This clobbers (over-writes) its parameter, so the change  
// is not reflected in the calling code.  
function Clobber(param)   
{  
    // clobber the parameter; this will not be seen in   
    // the calling code  
    param = new Object();  
    param.message = "This will not work";  
}  
  
// This modifies a property of the parameter, which  
// can be seen in the calling code.  
function Update(param)  
{  
    // Modify the property of the object; this will be seen  
    // in the calling code.  
    param.message = "I was changed";  
}  
  
// Create an object, and give it a property.  
var obj = new Object();  
obj.message = "This is the original";  
  
// Call Clobber, and print obj.message. Note that it hasn't changed.  
Clobber(obj);  
window.alert(obj.message); // Still displays "This is the original".  
  
// Call Update, and print obj.message. Note that is has changed.  
Update(obj);  
window.alert(obj.message); // Displays "I was changed".  
```  
  
## データのテスト  
 値によって比較する場合は、2 つの項目を比較して、互いに等しいかどうかを調べます。  通常、この比較はバイトごとに実行されます。  参照による比較を実行する場合は、2 つの項目が単一の元の項目へのポインターかどうかを調べます。  参照先の項目が同じである場合、両者は等しいと評価されます。参照先の項目が異なる場合は、値渡しで比較した場合に等しくなる値が格納されていても、両者は等しくないと評価されます。  
  
 参照渡しで文字列をコピーまたは受け渡すと、メモリを節約できますが、作成後に文字列を変更できないので、値渡しで比較できるようになります。  これにより、互いに個別に作成されている場合にも、2 つの文字列の内容が同じかどうかを調べることができます。  
  
## 参照  
 [日付と時刻の計算 \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md)