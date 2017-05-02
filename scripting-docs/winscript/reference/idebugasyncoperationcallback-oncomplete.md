---
title: "IDebugAsyncOperationCallBack::onComplete | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugAsyncOperationCallBack.onComplete
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugAsyncOperationCallBack::onComplete"
ms.assetid: d4023f5a-41f9-4948-b0dc-3317d61bb783
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugAsyncOperationCallBack::onComplete
結果は非同期のデバッグ操作から使用可能であることが示されます。  
  
## 構文  
  
```  
HRESULT onComplete();  
```  
  
#### パラメーター  
 このメソッドは、パラメーターを受け取りません。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、結果が `IDebugAsyncOperation` のオブジェクトから使用できることを通知します。  デバッガーのスレッドのイベントに適用されます。  
  
## 参照  
 [IDebugAsyncOperationCallBack インターフェイス](../../winscript/reference/idebugasyncoperationcallback-interface.md)   
 [IDebugAsyncOperation インターフェイス](../../winscript/reference/idebugasyncoperation-interface.md)