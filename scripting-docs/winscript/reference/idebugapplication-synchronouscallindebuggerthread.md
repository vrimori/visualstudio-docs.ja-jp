---
title: "IDebugApplication::SynchronousCallInDebuggerThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.SynchronousCallInDebuggerThread
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::SynchronousCallInDebuggerThread"
ms.assetid: 9daa1722-f25a-4691-aefc-fd28672fb883
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::SynchronousCallInDebuggerThread
デバッガーのスレッドで実行されるコードに呼び出し元に機構を提供します。  
  
## 構文  
  
```  
HRESULT SynchronousCallInDebuggerThread(  
   IDebugThreadCall*  pptc,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### パラメーター  
 `pptc`  
 \[入力\]呼び出すオブジェクト。  
  
 `dwParam1`  
 \[入力\] `IDebugThreadCall::ThreadCallHandler` メソッドにを渡す最初のパラメーター。  
  
 `dwParam2`  
 \[入力\] `IDebugThreadCall::ThreadCallHandler` メソッドにを渡す 2 番目のパラメーター。  
  
 `dwParam3`  
 \[入力\] `IDebugThreadCall::ThreadCallHandler` メソッドにを渡す 3 番目のパラメーター。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 言語のエンジンとホストは、通常、シングルスレッド実装の先頭にフリー スレッド オブジェクトを実装するために、このメソッドを使用します。  
  
## 参照  
 [IDebugApplication インターフェイス](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugThreadCall インターフェイス](../../winscript/reference/idebugthreadcall-interface.md)