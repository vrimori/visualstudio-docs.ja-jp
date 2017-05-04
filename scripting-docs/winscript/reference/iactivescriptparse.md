---
title: "IActiveScriptParse | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptParse インターフェイス"
ms.assetid: 8c967d70-f582-4f64-9e79-49f40c4dcb7c
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParse
Windows のスクリプト エンジンが生のテキストがコード スクリプトレット スクリプトに追加できるようにするか、または式のテキストが実行時に評価されるようにする場合 `IActiveScriptParse` のインターフェイスを実装します。  独立した編集環境が、VBScript などのスクリプト言語のない解釈されるため、スクリプト コードを、スクリプト エンジンに取得し、さまざまなオブジェクトのイベントにスクリプトのフラグメントをアタッチするための別の機構 \( `IPersist*`以外\) が用意されています。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IActiveScriptParse::InitNew](../../winscript/reference/iactivescriptparse-initnew.md)|スクリプト エンジンが初期化されます。|  
|[IActiveScriptParse::AddScriptlet](../../winscript/reference/iactivescriptparse-addscriptlet.md)|スクリプトにスクリプトレット コードを追加します。|  
|[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)|宣言を名前空間に追加し、必要に応じてコードを評価する特定のコード スクリプトレットを分析します。|  
  
## 参照  
 [アクティブ スクリプト インターフェイス](../../winscript/reference/active-script-interfaces.md)