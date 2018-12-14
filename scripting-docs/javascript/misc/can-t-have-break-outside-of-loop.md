---
title: 'break' をループの外に設定できません |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb23f1bc3de087515cad9ba4910cf2ebaf640353
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49928556"
---
# <a name="can39t-have-39break39-outside-of-loop"></a>'break' をループの外に設定できません
使用しようとする、 **break**ループ外にあるキーワード。 **Break**キーワードを使用して、ループの終了をまたは`switch`ステートメント。 ループの本体に埋め込む必要があります、または`switch`ステートメント。 ただし、**ラベル**break キーワードをフォローできます。  
  
```  
break labelname;  
```  
  
 ラベル付きののみ必要があります、 **break**入れ子になったループを使用しているときに、キーワードまたは`switch`ステートメントと最も内側のものではないループから抜け出す必要。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   確認、 **break**外側のループまたは switch ステートメント内でキーワードが表示されます。  
  
## <a name="see-also"></a>関連項目  
 [break ステートメント](../../javascript/reference/break-statement-javascript.md)   
 [プログラム フローの制御](../../javascript/controlling-program-flow-javascript.md)   
 [スクリプトのトラブルシューティング](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)
