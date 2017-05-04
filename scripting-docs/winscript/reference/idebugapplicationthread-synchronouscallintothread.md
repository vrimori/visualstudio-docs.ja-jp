---
title: "IDebugApplicationThread::SynchronousCallIntoThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationThread.SynchronousCallIntoThread
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplicationThread::SynchronousCallIntoThread"
ms.assetid: 8a91157f-dade-418a-ad02-5607ce12c95c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationThread::SynchronousCallIntoThread
アプリケーションのスレッドで実行されるコードに呼び出し元に機構を提供します。  
  
## 構文  
  
```  
HRESULT SynchronousCallIntoThread(  
   IDebugThreadCall*  pstcb,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### パラメーター  
 `pstcb`  
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
 このメソッドは、デバッガーのスレッドで実行されるコードに呼び出し元に機構を提供します。  言語のエンジンとホストは、通常、シングルスレッド実装の先頭にフリー スレッド オブジェクトを実装するために、このメソッドを使用します。  
  
## 参照  
 [IDebugApplicationThread インターフェイス](../../winscript/reference/idebugapplicationthread-interface.md)   
 [IDebugThreadCall インターフェイス](../../winscript/reference/idebugthreadcall-interface.md)