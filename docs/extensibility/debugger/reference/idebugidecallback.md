---
title: "IDebugIDECallback | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugIDECallback インターフェイス"
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugIDECallback
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されません。 CLR 式エバリュエーターの実装については、次を参照してください [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) と [マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 デバッガーの出力ウィンドウにメッセージを表示する式エバリュエーター \(EE\) を有効にします。  
  
## 構文  
  
```  
IDebugIDECallback : IUnknown  
```  
  
## 実装についてのメモ  
 このコールバックは、マネージ デバッグ エンジンによって実装されます。  
  
## 呼び出し元のノート  
 デバッガーの出力ウィンドウに出力を送信する式エバリュエーターでは使用できます。  
  
## メソッド  
 このインターフェイスには、次のメソッドを実装します。  
  
|メソッド|説明|  
|----------|--------|  
|[DisplayMessage](../Topic/IDebugIDECallback::DisplayMessage.md)|デバッガーの出力ウィンドウには、指定したメッセージ文字列を送信します。|  
  
## 必要条件  
 ヘッダー: Ee.h  
  
 名前空間: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll