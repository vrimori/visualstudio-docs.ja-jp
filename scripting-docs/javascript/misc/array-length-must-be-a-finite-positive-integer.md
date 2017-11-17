---
title: "配列の長さは、有限の正の整数である必要があります |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5029
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1a467040-4702-4178-848f-418a5974e907
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c6589bd2e9bb4acbec5f169087a49e64417dfae7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="array-length-must-be-a-finite-positive-integer"></a>配列の長さは、有限の正の整数でなければなりません。
呼び出しには、**配列**(0 と一連の正の整数の値は整数で構成されます) の整数ではない引数を持つコンス トラクターです。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   新たに作成する場合にのみ、正の整数を使用して`Array`オブジェクト。 整数でない 1 つの要素の配列を作成する場合は、2 段階のプロセスで行うことです。 1 つの要素を持つ配列を作成し、(array[0]) の最初の要素に値を配置します。 このエラーを生成する例を次に示します。  
  
    ```JavaScript  
    var piArray = new Array(3.14159);  
    ```  
  
     次の例では、1 つの数値要素の配列を指定するための正しい方法を示します。  
  
    ```JavaScript  
    var piArray = new Array(1);  
    piArray [0] = 3.14159;  
    ```  
  
     最大の整数値 (約 40億) 以外の配列のサイズの上限はありません。  
  
## <a name="see-also"></a>関連項目  
 [配列の使用](../../javascript/advanced/using-arrays-javascript.md)