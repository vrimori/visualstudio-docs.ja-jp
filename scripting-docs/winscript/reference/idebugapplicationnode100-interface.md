---
title: "IDebugApplicationNode100 インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationNode100 インターフェイス"
ms.assetid: 43966d4e-5f89-4a04-a08d-782347d00c2d
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugApplicationNode100 インターフェイス
`IDebugApplicationNode100` のインターフェイスは [IDebugApplicationNode インターフェイス](../../winscript/reference/idebugapplicationnode-interface.md)の機能を拡張します。  [IDebugApplicationNode インターフェイス](../../winscript/reference/idebugapplicationnode-interface.md)の実装の QueryInterface を呼び出して、このインターフェイスのインスタンスを取得できます。  
  
> [!IMPORTANT]
>  このインターフェイスは PDM v10.0 を超えるによって実装されます。  activdbg100.h.である。  
  
## メソッド  
 `IDebugApplicationNode100` インターフェイスは、以下のメソッドを公開します。  
  
|メソッド|説明|  
|----------|--------|  
|[IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md)|指定したフィルターによって非表示になっているテキスト ドキュメントを取得します。|  
|[IDebugApplicationNode100::QueryIsChildNode](../../winscript/reference/idebugapplicationnode100-queryischildnode.md)|指定されたドキュメントがこのノードの子ノードの 1 に属するかどうかを判断します。|  
|[IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)|[IDebugApplicationNodeEvents インターフェイス](../../winscript/reference/idebugapplicationnodeevents-interface.md) の特定の実装のフィルターを設定します。  これにより、ノードを作成または削除されたとき PDM が既にイベントを送信しないようにスクリプト デバッガーがコンパイラにより生成された子アプリケーションのノードを除外することができます。  既定では、すべてのノードが送信されます。|