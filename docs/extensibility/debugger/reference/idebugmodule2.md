---
title: "IDebugModule2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModule2"
helpviewer_keywords: 
  - "IDebugModule2 インターフェイス"
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugModule2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはモジュールDLL としてこのようなプログラムの実行単位表します。  
  
## 構文  
  
```  
IDebugModule2 : IUnknown  
```  
  
## 実装についてのメモ  
 デバッグ エンジンは \(DE\)モジュールを表しそのモジュールに関する情報へのアクセスを提供するにはこのインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) の呼び出しはこのインターフェイスを返します。  DE sends [イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) メソッドを使用してデバッグ セッションの [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) マネージャー \(SDM\) へのインターフェイス。  
  
 このインターフェイスはで返す返される\) [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) の構造体 \([EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) 呼び出しによってできます。  
  
 [次へ](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) はこのインターフェイスを返します。[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) は [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) のインターフェイスを返します\)。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugModule2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|を取得します [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) このモジュールを表す。|  
|[ReloadSymbols\_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|互換性のために残されています。  使用しないでください。  このモジュールのシンボルを再読み込みします。|  
  
## 解説  
 モジュールの情報はIDE の \[ENT0ENT\] ウィンドウで表示できます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)