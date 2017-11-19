---
title: "VBArray が必要です |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5013
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f2998d7d-13a4-4bbe-b872-3ff3316551e4
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b07c5e08e4178c9c31045317627424f5192f5e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="vbarray-expected"></a>VBArray が必要です。
1 つが予想される場合、Visual Basic safeArray れていないオブジェクトを指定しています。  
  
```  
new VBArray(safeArray);  
```  
  
 VBArrays は読み取り専用で、直接作成することはできません。 SafeArray 引数は、VBArray 値に渡される前に VBArray 値を取得する必要がありますが、`VBArray`コンス トラクターです。 この操作は、既存の ActiveX またはその他のオブジェクトから値を取得することによってのみ行うことができます。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   のみを渡すことを確認**VBArray**オブジェクトを**VBArray**コンス トラクターです。  
  
## <a name="see-also"></a>関連項目  
 [VBArray オブジェクト](../../javascript/reference/vbarray-object-javascript.md)   
 [配列の使用](../../javascript/advanced/using-arrays-javascript.md)