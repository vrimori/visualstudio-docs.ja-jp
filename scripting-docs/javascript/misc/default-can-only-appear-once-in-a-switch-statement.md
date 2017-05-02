---
title: "&#39;default&#39; は &#39;switch&#39; ステートメントのなかに、一度のみ表示できます。 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT1027"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: a94100f4-6ee5-4759-b635-9d309e47111e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# &#39;default&#39; は &#39;switch&#39; ステートメントのなかに、一度のみ表示できます。
switch ステートメント内で **default** ステートメントを複数回使用しようとしました。  既定のケースは、常に switch ステートメントの最後の case ステートメントです （フォールスルー ケース）。  
  
### このエラーを解決するには  
  
-   `switch` ステートメントから余分な **default** case ステートメントを削除します。switch ステートメントで使用する default case ステートメントは 1 つだけにしてください。  
  
## 参照  
 [switch ステートメント](../../javascript/reference/switch-statement-javascript.md)   
 [プログラム フローの制御](../../javascript/controlling-program-flow-javascript.md)   
 [JavaScript の予約語](../../javascript/reference/javascript-reserved-words.md)