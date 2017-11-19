---
title: "例外がスローされ、キャッチされませんでした |。Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5022
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 839ff08da4d26406b508a206c809b0813d2b32e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="exception-thrown-and-not-caught"></a>例外がスローされ、キャッチされませんでした。
含まれている、`throw`内では、コード内のステートメントが囲まれていない、**を再試行してください**ブロック、か、関連付けられていませんが**キャッチ**エラーをトラップするブロック。 内から例外がスローされます、**を再試行してください**ブロックを使用して、**スロー**ステートメントでは、外部キャッチし、**を再試行してください**ブロックを**キャッチ**ステートメント。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   例外をスローするコードを囲む、**を再試行してください**がありますが、対応することを確認して、ブロック**キャッチ**ブロックします。  
  
-   Catch ステートメントに正しい形式の例外が必要ですが確認してください。  
  
-   例外が再度スローされ場合、は、別の対応する catch ステートメントがあることを確認してください。  
  
## <a name="see-also"></a>関連項目  
 [Error オブジェクト](../../javascript/reference/error-object-javascript.md)   
 [throw ステートメント](../../javascript/reference/throw-statement-javascript.md)   
 [try… catch… finally ステートメント](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)