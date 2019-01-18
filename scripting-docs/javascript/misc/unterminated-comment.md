---
title: コメントがありません |Microsoft Docs
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
- VS.WebClient.Help.SCRIPT1016
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d4286315-814b-4966-b4c4-1ee19d796eff
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9fde5d5edd7e81060b088e4940d752aa05e65ded
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348184"
---
# <a name="unterminated-comment"></a>未終了のコメントです。
複数行のコメント ブロックを開始しましたが、正常に終了しませんでしたが。 複数行コメントが始まる、"/\*"逆で終わると組み合わせ、"\*/"の組み合わせ。 次に例を示します。  
  
```JavaScript  
/* This is a comment  
This is another part of the same comment.*/  
```  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   複数行コメントが終了することを確認する"*/"。  
  
## <a name="see-also"></a>関連項目  
 [コメント ステートメント](../../javascript/reference/comment-statements-javascript.md)