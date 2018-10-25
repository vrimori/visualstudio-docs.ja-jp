---
title: 条件付きコンパイルは無効になります |Microsoft Docs
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
- VS.WebClient.Help.SCRIPT1030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f2eabb900e24072c8f390061b5d6081de9bc889
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49914243"
---
# <a name="conditional-compilation-is-turned-off"></a>条件付きコンパイルは無効になっています。
初めてオンにする条件付きコンパイルなしの条件付きコンパイル変数を使用しようとしました。 通知の条件付きコンパイルの有効化、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]コンパイラに条件付きコンパイル変数としてで始まる識別子。 条件付きステートメントを使用してコードを開始することで行います。  
  
```  
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   条件付きコードの先頭に次のステートメントを追加します。  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>関連項目  
 [条件付きコンパイル](../../javascript/advanced/conditional-compilation-javascript.md)   
 [条件付きコンパイル変数](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_on ステートメント](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if ステートメント](../../javascript/reference/at-if-statement-javascript.md)   
 [@set ステートメント](../../javascript/reference/at-set-statement-javascript.md)