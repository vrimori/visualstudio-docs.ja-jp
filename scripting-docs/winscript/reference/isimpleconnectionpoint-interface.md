---
title: "ISimpleConnectionPoint インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "ISimpleConnectionPoint インターフェイス"
ms.assetid: f632a82f-942d-4291-963e-e9fa2b162493
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ISimpleConnectionPoint インターフェイス
特定のコネクション ポイントで発生したイベントについて説明し、列挙する単純な方法を提供します。  このインターフェイスは、これらのイベントに `IDispatch` のオブジェクトをフックも容易になります。  このインターフェイスは、プロセスのデバッグ Manager \(PDM\) によって実装され、スクリプト エンジンによって実装されます。  
  
 このインターフェイスは `IDebugHelper::CreateSimpleConnectionPoint`から使用できます。  
  
 `IUnknown` から継承するメソッドに加え、`ISimpleConnectionPoint` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|単純なコネクション ポイント オブジェクトとクライアント シンク間の接続を確立します。|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|イベントの指定範囲の各イベントの DISPID と名前を返します。|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|このインターフェイスで公開されるイベント数を返します。|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|`ISimpleConnectionPoint::Advise` が以前に確立したアドバイザリ コネクションを終了します。|  
  
## 参照  
 [IDebugProperty インターフェイス](../../winscript/reference/idebugproperty-interface.md)