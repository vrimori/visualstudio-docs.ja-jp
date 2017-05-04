---
title: "IDebugApplicationThread インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationThread インターフェイス"
ms.assetid: f869c328-4409-4b74-a6c3-9e63fc58c63d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationThread インターフェイス
言語のエンジンとホストがスレッドの同期を提供し、スレッド固有のデバッグ状態情報を管理します。  このインターフェイスは、スレッドへの非リモートのアクセスを提供するために `IRemoteDebugApplicationThread` のインターフェイスを拡張します。  
  
 `IRemoteDebugApplicationThread` から継承するメソッドに加え、`IDebugApplicationThread` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IDebugApplicationThread::SynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread-synchronouscallintothread.md)|アプリケーションのスレッドで実行されるコードに呼び出し元に機構を提供します。|  
|[IDebugApplicationThread::QueryIsCurrentThread](../../winscript/reference/idebugapplicationthread-queryiscurrentthread.md)|このスレッドが現在実行中のスレッドかどうかを判定します。|  
|[IDebugApplicationThread::QueryIsDebuggerThread](../../winscript/reference/idebugapplicationthread-queryisdebuggerthread.md)|このスレッドがデバッガーのスレッドかどうかを判定します。|  
|[IDebugApplicationThread::SetDescription](../../winscript/reference/idebugapplicationthread-setdescription.md)|このスレッドの説明を設定します。|  
|[IDebugApplicationThread::SetStateString](../../winscript/reference/idebugapplicationthread-setstatestring.md)|スレッド状態の説明を設定します。|