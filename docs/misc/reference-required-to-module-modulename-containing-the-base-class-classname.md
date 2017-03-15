---
title: "基底クラス &#39;&lt;classname&gt;&#39; を含む &#39;&lt;modulename&gt;&#39; モジュールへの参照が必要です | Microsoft Docs"
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
  - "vbc30008"
  - "bc30008"
helpviewer_keywords: 
  - "BC30008"
ms.assetid: ec8de475-8a8b-4aa5-86c9-6fcc44dcec06
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 基底クラス &#39;&lt;classname&gt;&#39; を含む &#39;&lt;modulename&gt;&#39; モジュールへの参照が必要です
基底クラス '\<classname\>' を含む '\<modulename\>' モジュールへの参照が必要です。 プロジェクトに参照を追加してください。  
  
 プロジェクト内で直接参照されないモジュールでクラスが定義されています。[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] コンパイラでは、クラスが複数のモジュールで定義されている場合に備えて、あいまいさを避けるために参照が必要になります。  
  
 **エラー ID:** BC30008  
  
### このエラーを解決するには  
  
-   参照されていないモジュールの名前をプロジェクト参照に含めます。  
  
## 参照  
 [NIB: 名前空間およびコンポーネントの参照](http://msdn.microsoft.com/ja-jp/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [壊れた参照のトラブルシューティング](../ide/troubleshooting-broken-references.md)