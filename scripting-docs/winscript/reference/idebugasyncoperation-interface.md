---
title: "IDebugAsyncOperation インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugAsyncOperation インターフェイス"
ms.assetid: ebb2ea75-1443-4d8a-812d-171a166f5f9d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugAsyncOperation インターフェイス
プロセス デバッグ マネージャーは `IDebugAsyncOperation` のインターフェイスを実装します。  言語エンジンは、このインターフェイスへの参照を取得するに `IDebugApplication::CreateAsyncDebugOperation` のメソッドを呼び出します。  同期エンジンは、言語のデバッグ操作への非同期アクセスするために `IDebugAsyncOperation` のインターフェイスを使用できます。  
  
 `IUnknown` から継承するメソッドに加え、`IDebugAsyncOperation` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IDebugAsyncOperation::GetSyncDebugOperation](../../winscript/reference/idebugasyncoperation-getsyncdebugoperation.md)|このオブジェクトに関連付けられた同期デバッグ操作を返します。|  
|[IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)|非同期操作を開始します。|  
|[IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)|操作をキャンセルします。|  
|[IDebugAsyncOperation::QueryIsComplete](../../winscript/reference/idebugasyncoperation-queryiscomplete.md)|デバッグ操作が完了したかどうかを判定します。|  
|[IDebugAsyncOperation::GetResult](../../winscript/reference/idebugasyncoperation-getresult.md)|同期デバッグ操作からの戻り値と、オブジェクトのパラメーターを指定します。|