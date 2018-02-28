---
title: "&#39; が t &#39; 中断 &#39;ループの外 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb23f1bc3de087515cad9ba4910cf2ebaf640353
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="can39t-have-39break39-outside-of-loop"></a>&#39; が t &#39; 中断 &#39;ループの外
使用しようとする、 **break**ループの外側のキーワードです。 **Break**ループを終了するキーワードを使用または`switch`ステートメントです。 ループの本体に埋め込まれている必要がありますまたは`switch`ステートメントです。 ただし、**ラベル**break キーワードに従うことができます。  
  
```  
break labelname;  
```  
  
 ラベル付きののみが必要、 **break**キーワードを使用しているときにループが入れ子になったまたは`switch`ステートメントと最も内側のものではないループから抜ける必要があります。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   確認、 **break**キーワードが外側のループまたは switch ステートメントの内側に表示されます。  
  
## <a name="see-also"></a>関連項目  
 [break ステートメント](../../javascript/reference/break-statement-javascript.md)   
 [プログラム フローの制御](../../javascript/controlling-program-flow-javascript.md)   
 [スクリプトのトラブルシューティング](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)