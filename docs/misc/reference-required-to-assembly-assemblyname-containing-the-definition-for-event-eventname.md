---
title: "イベント &#39;&lt;eventname&gt;&#39; の定義を含むアセンブリ &#39;&lt;assemblyname&gt;&#39; への参照が必要です | Microsoft Docs"
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
  - "vbc30005"
  - "bc30005"
helpviewer_keywords: 
  - "BC30005"
ms.assetid: 843b0b2f-0f93-41c3-8727-13a2138e8140
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# イベント &#39;&lt;eventname&gt;&#39; の定義を含むアセンブリ &#39;&lt;assemblyname&gt;&#39; への参照が必要です
イベント '\<`eventname`\>' の定義を含むアセンブリ '\<`assemblyname`\>' への参照が必要です。 プロジェクトへの参照を追加します。  
  
 プロジェクト内で直接参照されないダイナミック リンク ライブラリ \(DLL\) またはアセンブリでイベントが定義されています。[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] コンパイラでは、イベントが複数の DLL またはアセンブリで定義されている場合に備えて、あいまいさを避けるための参照が必要になります。  
  
 **エラー ID:** BC30005  
  
### このエラーを解決するには  
  
-   参照されない DLL またはアセンブリの名前をプロジェクト参照に含めます。  
  
## 参照  
 [NIB: 名前空間およびコンポーネントの参照](http://msdn.microsoft.com/ja-jp/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [壊れた参照のトラブルシューティング](../ide/troubleshooting-broken-references.md)