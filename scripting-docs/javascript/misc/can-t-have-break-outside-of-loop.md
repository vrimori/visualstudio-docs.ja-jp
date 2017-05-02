---
title: "&#39;break&#39; をループの外に設定できません。 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1019"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# &#39;break&#39; をループの外に設定できません。
ループの外側で **break** のキーワードを使用しようとしました。  **break** キーワードは、ループまたは `switch` ステートメントを終了するために使用されます。  これは、ループまたは `switch` ステートメントの中に埋め込む必要があります。  ただし、break キーワードの後に **label** を指定することができます。  
  
```  
break labelname;  
```  
  
 **break** キーワードでラベルの指定が必要になるのは、入れ子になったループまたは `switch` ステートメントで、最も内側ではないループを終了する必要があるときだけです。  
  
### このエラーを解決するには  
  
-   **break** キーワードがそれを囲むループまたは switch ステートメントの内側にあることを確認します。  
  
## 参照  
 [break ステートメント](../../javascript/reference/break-statement-javascript.md)   
 [プログラム フローの制御](../../javascript/controlling-program-flow-javascript.md)   
 [JScript スクリプトのトラブルシューティング](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)