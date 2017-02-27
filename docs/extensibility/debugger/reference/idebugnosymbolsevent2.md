---
title: "IDebugNoSymbolsEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugNoSymbolsEvent2 インターフェイス"
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugNoSymbolsEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

シンボルが起動する実行可能ファイルに検出できないと [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] デバッガーの UI をユーザーに通知するように通知します。  
  
## 構文  
  
```  
IDebugNoSymbolsEvent2 : IUnknown  
```  
  
## 実装についてのメモ  
 デバッグ エンジンによって実装され[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] デバッガーの UI によって実装されます。  
  
## 必要条件  
 ヘッダー : Msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll