---
title: "配列の使用 (JavaScript) | Microsoft Docs"
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
  - "配列 [JavaScript]"
  - "配列 [JavaScript], オブジェクト"
ms.assetid: 785c5acd-b8b3-4152-af9a-dd42ecdd75ba
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# 配列の使用 (JavaScript)
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] の配列は*疎配列*です。  つまり、0、1、および 2 の 3 つの要素を含む配列がある場合、要素 3 から 49 を意識せずに要素 50 を作成できます。  配列に自動的に更新される length 変数 （配列の長さの自動監視の詳細については、「[組み込みオブジェクト](../../javascript/intrinsic-objects-javascript.md)」を参照） がある場合、length 変数は 4 ではなく 51 に設定されます。  要素の番号付けにギャップを空けない配列を作成できますが、必ずしもそうする必要はありません。  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] では、オブジェクトおよび配列はほとんど同じです。  主な違いは、非配列オブジェクトには自動的に更新される length プロパティがない点と、配列にはプロパティとメソッドがない点の 2 つです。  
  
## 配列のアドレス指定  
 次の例に示すように、配列のアドレスは角かっこ （\[\]） を使用して指定します。  角かっこ内には、数値または整数に評価される式を含めます。  
  
```javascript  
var entryNum = 5;  
  
sample = new Array();  
  
sample[1] = "Maple Street";  
sample[entryNum] = 25;  
  
document.write (sample[1]);  
document.write (" ");  
document.write (sample[entryNum]);  
  
// Output: Maple Street 25  
  
```  
  
## 連想配列としてのオブジェクト  
 オブジェクトのプロパティには、一般にドット演算子 "." を使用してアクセスします。  次に例を示します。  
  
```javascript  
myObject.aProperty  
```  
  
 この場合、プロパティ名は識別子です。  オブジェクトのプロパティには、添字演算子 \(\[\]\) を使用してアクセスすることもできます。  この場合、データ値が文字列に関連付けられた*連想配列*としてオブジェクトを扱っていることになります。  次に例を示します。  
  
```javascript  
myObject["aProperty"] // Same as above.  
```  
  
 添字演算子は、配列の要素にアクセスするために使用するのがより一般的です。  これをオブジェクトに対して使用する場合、インデックスはプロパティ名を表す文字列リテラルです。  
  
 オブジェクトのプロパティにアクセスするこの 2 つの方法には、次の表に示すように重要な違いがあります。  
  
1.  識別子 \(ドット \(.\) 構文\) として扱うプロパティ名をデータとして扱うことはできません。  
  
2.  インデックス \(角かっこ \(\[\]\) 構文\) として扱うプロパティ名は、データとして扱うことができます。  
  
 この違いは、ユーザーの入力内容に基づいてオブジェクトを作成する場合など、実行時までプロパティ名がわからない場合に有用です。  連想配列からすべてのプロパティを抽出するには、`for…in` ループを使用する必要があります。