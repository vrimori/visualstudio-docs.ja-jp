---
title: "実装されたインターフェイス &#39;&lt;interfacename&gt;&#39; を含むモジュール &#39;&lt;modulename&gt;&#39; への参照が必要です | Microsoft Docs"
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
  - "vbc30010"
  - "bc30010"
helpviewer_keywords: 
  - "BC30010"
ms.assetid: 57fe7e15-bf99-49d1-ba6c-bb7abeb615b1
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 実装されたインターフェイス &#39;&lt;interfacename&gt;&#39; を含むモジュール &#39;&lt;modulename&gt;&#39; への参照が必要です
実装されたインターフェイス '\<interfacename\>' を含むモジュール '\<modulename\>' への参照が必要です。 プロジェクトに参照を追加してください。  
  
 プロジェクト内で直接参照されないモジュールでインターフェイスが定義されています。[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] コンパイラでは、インターフェイスが複数のモジュールで定義されている場合に備えて、あいまいさを避けるための参照が必要になります。  
  
 **エラー ID:** BC30010  
  
### このエラーを解決するには  
  
-   参照されていないモジュールの名前をプロジェクト参照に含めます。  
  
## 参照  
 [NIB: 名前空間およびコンポーネントの参照](http://msdn.microsoft.com/ja-jp/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [壊れた参照のトラブルシューティング](../ide/troubleshooting-broken-references.md)