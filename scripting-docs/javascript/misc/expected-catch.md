---
title: 予想 &#39; catch &#39; |Microsoft ドキュメント
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
- VS.WebClient.Help.SCRIPT1033
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6cd1e57137d220ebcf3834070e36d8257e2dca7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633792"
---
# <a name="expected-39catch39"></a>予想 &#39; catch &#39;
例外処理を使用した**を再試行してください**ブロックしますが、関連付けられている書き込めませんでした**キャッチ**ステートメントです。 例外処理メカニズムでは、内側に失敗し、例外が発生するときに実行する必要がありますしないコードと共に、コードに記述する必要があります、**再試行**ブロックします。 内から例外がスローされます、**を再試行してください**ブロックを使用して、**スロー**ステートメントでは、外部キャッチし、**を再試行してください**と 1 つ以上のブロック**をキャッチ**ステートメントです。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   関連付けられた追加**キャッチ**ブロックします。  
  
-   使用してみて、**最後に**ブロックの代わりに、**キャッチ**ブロックします。  
  
## <a name="see-also"></a>関連項目  
 [try… catch... 最後にステートメント](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Error オブジェクト](../../javascript/reference/error-object-javascript.md)