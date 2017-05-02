---
title: "IDebugThreadCall インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugThreadCall インターフェイス"
ms.assetid: 9a9a9892-f310-4ef3-8db2-4f868be52d7e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugThreadCall インターフェイス
`IDebugThreadCall` のインターフェイスは、プロセス デバッグ Manager \(PDM\) が提供する実装を配置する `IDebugThread` のスレッド間の呼び出しを行うコンポーネントによって正常に実行されます。  
  
 PDM は、目的のスレッドの `IDebugThreadCall` のインターフェイスを呼び出し、`IDebugThreadCall` のインターフェイスは、目的の実装に呼び出しをディスパッチします。  `IDebugThreadCall` のインターフェイスは、適切な上にパラメーターを渡すパラメーター情報をキャストします。  
  
 `IDebugThreadCall` のインターフェイスは、フリー スレッド オブジェクトです。  
  
## メソッド  
 `IUnknown` から継承するメソッドに加え、`IDebugThreadCall` インターフェイスは次のメソッドを公開します。  
  
|メソッド|説明|  
|----------|--------|  
|[IDebugThreadCall::ThreadCallHandler](../../winscript/reference/idebugthreadcall-threadcallhandler.md)|別のスレッドでコードを実行するハンドルを呼び出します。|