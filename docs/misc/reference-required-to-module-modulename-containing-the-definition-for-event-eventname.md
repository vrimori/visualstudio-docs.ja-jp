---
title: "イベント &#39;&lt;eventname&gt;&#39; の定義を含むモジュール &#39;&lt;modulename&gt;&#39; への参照が必要です | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30006"
  - "bc30006"
helpviewer_keywords: 
  - "BC30006"
ms.assetid: 7ab80acd-b47b-4920-bb15-6a3206b984e4
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# イベント &#39;&lt;eventname&gt;&#39; の定義を含むモジュール &#39;&lt;modulename&gt;&#39; への参照が必要です
イベント '\<`eventname`\>' の定義を含むモジュール '\<`modulename`\>' への参照が必要です。 プロジェクトに参照を追加してください。  
  
 プロジェクト内で直接参照されないモジュールでイベントが定義されています。[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] コンパイラでは、イベントが複数のモジュールで定義されている場合に備えて、あいまいさを避けるために参照が必要になります。  
  
 **エラー ID:** BC30006  
  
### このエラーを解決するには  
  
-   参照されないモジュールの名前をプロジェクト参照に含めます。  
  
## 参照  
 [NIB: 名前空間およびコンポーネントの参照](http://msdn.microsoft.com/ja-jp/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [壊れた参照のトラブルシューティング](../ide/troubleshooting-broken-references.md)