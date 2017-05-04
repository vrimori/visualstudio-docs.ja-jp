---
title: "IActiveScriptParseProcedureOld インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParseProcedureOld
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptParseProcedureOld インターフェイス"
ms.assetid: d94b391e-4c24-46da-a01f-2c134ca4f041
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptParseProcedureOld インターフェイス
プロシージャのソース・コード テキストのスクリプトに追加できます。  独立した編集環境が、VBScript などのスクリプト言語のない解釈されるため、名前空間、スクリプトのプロシージャを追加するために別の機構を `IActiveScriptParse` \(または `IPersist*`以外\) が用意されています。  
  
> [!NOTE]
>  このインターフェイスは、インターフェイスを `IActiveScriptParseProcedure` の使用は推奨されません。  
  
## メソッド  
 `IUnknown` から継承するメソッドに加え、`IActiveScriptParseProcedureOld` インターフェイスは次のメソッドを公開します。  
  
|メソッド|説明|  
|----------|--------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|特定のプロシージャ コードを分析し、名前空間にプロシージャを追加します。|  
  
## 参照  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)