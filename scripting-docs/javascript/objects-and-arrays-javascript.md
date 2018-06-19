---
title: オブジェクトと配列 (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arrays [JavaScript]
- arrays [JavaScript], objects
ms.assetid: f5106284-1240-4f47-8c3b-5a45e227e5e1
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6776701ba108ae0ecefc2331c2b12272e0c1be19
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569342"
---
# <a name="objects-and-arrays-javascript"></a>オブジェクトと配列 (JavaScript)
[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] のオブジェクトは、プロパティとメソッドのコレクションです。 メソッドは、オブジェクトのメンバーとなっている関数です。 プロパティは、オブジェクトのメンバーである値または値のセット (配列やオブジェクト) です。 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] では、次の 4 種類のオブジェクトがサポートされます。  
  
-   組み込みオブジェクト (`Array`、`String` など)。  
  
-   ユーザーが作成したオブジェクト。  
  
-   ホスト オブジェクト (`window`、`document` など)。  
  
-   ActiveX オブジェクト。  
  
## <a name="expando-properties-and-methods"></a>Expando プロパティおよびメソッド  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] のすべてのオブジェクトは、実行時に追加および削除できる expando プロパティおよびメソッドをサポートします。 これらのプロパティおよびメソッドには、任意の名前を指定でき、数字で識別できます。 プロパティまたはメソッドの名前が単純な識別子の場合、オブジェクト名およびそれに続くピリオドの後に記述できます。たとえば、次のコードの `myObj.name`, `myObj.age` および `myObj.getAge` などです。  
  
```JavaScript  
var myObj = new Object();  
myObj.name = "Fred";  
myObj.age = 42;  
  
myObj.getAge =   
    function () {  
        return this.age;  
    };  
  
document.write(myObj.name);  
document.write("<br/>");  
document.write(myObj.age);  
document.write("<br/>");  
document.write(myObj.getAge());  
  
// Output:  
// Fred  
// 42  
// 42  
  
```  
  
 プロパティまたはメソッドの名前が単純な識別子ではない場合、またはスクリプトを記述する時点でわからない場合、任意の式を角かっこで囲んでプロパティにインデックスを付けることができます。 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] のすべての expando プロパティの名前は、オブジェクトに追加される前に文字列に変換されます。  
  
```JavaScript  
var myObj = new Object();  
  
// Add two expando properties that cannot be written in the  
// object.property syntax.  
// The first contains invalid characters (spaces), so must be  
// written inside square brackets.  
myObj["not a valid identifier"] = "This is the property value";  
  
// The second expando name is a number, so it also must  
// be placed inside square brackets  
myObj[100] = "100";  
```  
  
 定義からのオブジェクトの作成については、「[オブジェクトの作成](../javascript/creating-objects-javascript.md)」をご覧ください。  
  
## <a name="arrays-as-objects"></a>オブジェクトとしての配列  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] では、配列は単なる特別な種類のオブジェクトであるため、オブジェクトと配列はほとんど同じように扱われます。 オブジェクトと配列は、どちらもプロパティおよびメソッドを持つことができます。  
  
 配列には `length` プロパティがありますが、オブジェクトにはありません。 インデックスが長さを超える (たとえば、`myArray[100] = "hello"`) 配列の要素に値を割り当てると、`length` プロパティは、新しい長さに自動的に増加します。 同様に `length` プロパティを小さくすると、インデックスが配列の長さの外部にあるすべての要素が削除されます。  
  
```JavaScript  
// An array with three elements  
var myArray = new Array(3);  
  
// Add some data  
myArray[0] = "Hello";  
myArray[1] = 42;  
myArray[2] = new Date(2000, 1, 1);  
  
document.write("original length is: " + myArray.length);  
document.write("<br/>");  
// Add some expando properties  
myArray.expando = "JavaScript!";  
myArray["another Expando"] = "Windows";  
  
// This will still display 3, since the two expando properties  
// don't affect the length.  
document.write("new length is : " + myArray.length);  
  
// Output:  
// original length is: 3  
// new length is : 3  
  
```  
  
 配列は反復処理を行うメソッドを提供し、メンバーを操作します。 配列に格納されたオブジェクトのプロパティを取得する方法を次の例に示します。  
  
```JavaScript  
var myArray = new Array(3);  
  
// Add some data  
for(var i = 1; i <= 3; i++) {  
    myArray[i] = new Date(2000 + i, 1, 1);  
}  
  
myArray.forEach(function (item) {  
    document.write(item.getFullYear());  
});  
  
// Output:  
// 2001  
// 2002  
// 2003  
```  
  
## <a name="multi-dimensional-arrays"></a>多次元配列  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] は多次元配列を直接サポートしませんが、別の配列の要素に配列を格納すると、多次元配列の動作を実現できます。 (他の配列を含むあらゆる種類のデータを配列の要素内に格納できます。)たとえば、次のコードは、5 までの乗算テーブルを作成します。  
  
```JavaScript  
// The size of the table.  
var iMaxNum = 5;  
// Loop counters.  
var i, j;  
  
// Set the length of the array to iMaxNum + 1.   
// The first array index is zero, not 1.  
var MultiplicationTable = new Array(iMaxNum + 1);  
  
// Loop for each major number (each row in the table)  
for (i = 1; i <= iMaxNum; i++)  
{  
    // Create the columns in the table  
    MultiplicationTable[i] = new Array(iMaxNum + 1);  
  
    // Fill the row with the results of the multiplication  
    for (j = 1; j <= iMaxNum; j++)  
    {  
        MultiplicationTable[i][j] = i * j;  
    }  
}  
  
document.write(MultiplicationTable[3][4]);  
document.write("<br/>");   
document.write(MultiplicationTable[5][2]);  
document.write("<br/>");  
document.write(MultiplicationTable[1][4]);  
  
// Output:  
// 12  
// 10  
// 4  
  
```