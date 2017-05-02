---
title: "IActiveScriptParseProcedure | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptParseProcedure インターフェイス"
ms.assetid: 741a35bb-5b92-489e-ba8a-a406b42125fc
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParseProcedure
Windows のスクリプト エンジンがプロシージャのソース・コード テキストのスクリプトに追加する場合 `IActiveScriptParseProcedure` のインターフェイスを実装します。  独立した編集環境が、VBScript などのスクリプト言語のない解釈される場合、これは別の機構 \( `IActiveScriptParse` または名前空間以外 `IPersist`\*、スクリプトのプロシージャを追加する場合\) が用意されています。  
  
## Vtable 順序のメソッド  
  
|||  
|-|-|  
|メソッド|説明|  
|[IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)|特定のプロシージャ コードを分析し、名前空間にプロシージャを追加します。|  
  
## 参照  
 [アクティブ スクリプト インターフェイス](../../winscript/reference/active-script-interfaces.md)