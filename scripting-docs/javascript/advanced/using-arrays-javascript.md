---
title: "配列の使用 (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arrays [JavaScript]
- arrays [JavaScript], objects
ms.assetid: 785c5acd-b8b3-4152-af9a-dd42ecdd75ba
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c5218a8353a796128d8b672ecc781665c6bde20
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="using-arrays-javascript"></a>配列の使用 (JavaScript)
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 内の配列は*スパース*です。 つまり、0、1、および 2 の 3 つの要素を含む配列がある場合、要素 3 から 49 を意識せずに要素 50 を作成できます。 配列に自動変数 length が存在する場合 (配列の長さの自動監視の詳細については、「[組み込みオブジェクト (JavaScript)](../../javascript/intrinsic-objects-javascript.md)」を参照してください)、length 変数は 4 ではなく、51 に設定されます。 要素の番号付けで番号が飛ばない配列を作成できますが、必ずしもそうする必要はありません。  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] では、オブジェクトと配列はほとんど同じです。 主な違いは、非配列オブジェクトには自動プロパティ length がない点と、配列にはオブジェクトのプロパティとメソッドがない点の 2 つです。  
  
## <a name="addressing-arrays"></a>配列のアドレス指定  
 以下の例に示すように、角かっこ ([]) を使用して配列をアドレス指定します。 角かっこで、整数に評価される式または数値を囲みます。  
  
```JavaScript  
var entryNum = 5;  
  
sample = new Array();  
  
sample[1] = "Maple Street";  
sample[entryNum] = 25;  
  
document.write (sample[1]);  
document.write (" ");  
document.write (sample[entryNum]);  
  
// Output: Maple Street 25  
  
```  
  
## <a name="objects-as-associative-arrays"></a>連想配列としてのオブジェクト  
 オブジェクトのプロパティにアクセスする場合は、一般にドット演算子 "." を使用します。 次に例を示します。  
  
```JavaScript  
myObject.aProperty  
```  
  
 この場合、プロパティ名は識別子です。 インデックス演算子 ([]) を使用して、オブジェクトのプロパティにアクセスすることもできます。 この場合、データ値が文字列に関連付けられた*連想配列*としてオブジェクトを扱っていることになります。 次に例を示します。  
  
```JavaScript  
myObject["aProperty"] // Same as above.  
```  
  
 インデックス演算子は、配列要素へのアクセスに関連するのがより一般的です。 これをオブジェクトで使用する場合、インデックスはプロパティ名を表す文字列リテラルとなります。  
  
 オブジェクト プロパティにアクセスするための 2 つの方法には重要な違いがあることに注意してください。  
  
1.  識別子 (ドット (.) 構文) のように扱われるプロパティ名をデータのように扱うことはできません。  
  
2.  インデックス (中かっこ ([]) 構文) のように扱われるプロパティ名をデータのように扱うことができます。  
  
 この違いは、(ユーザーの入力内容に基づいてオブジェクトを作成する場合など) 実行時までプロパティ名がわからない場合に有用です。 連想配列からすべてのプロパティを抽出する場合は、`for...in` ループを使用する必要があります。