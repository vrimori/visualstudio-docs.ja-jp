---
title: "IDebugAsyncOperation::GetResult | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugAsyncOperation.GetResult
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugAsyncOperation::GetResult"
ms.assetid: 56d43365-6b12-4213-a97c-953c40d7b7f6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugAsyncOperation::GetResult
同期デバッグ操作からの戻り値と、オブジェクトのパラメーターを指定します。  
  
## 構文  
  
```  
HRESULT GetResult(  
   HRESULT*    phrResult,  
   IUnknown**  ppunkResult  
);  
```  
  
#### パラメーター  
 `phrResult`  
 操作が終わったら、\[入力\] `phrResult` は `IDebugSyncOperation::Execute`の戻り値です。  
  
 `ppunkResult`  
 操作が終わったら、\[入力\] `ppunkResult` は、操作によって返されるオブジェクトのパラメーターです。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
|`E_PENDING`|操作は完了していません。|  
  
## 解説  
 操作完了に、このメソッドは `HRESULT` と `IDebugSyncOperation::Execute`からオブジェクトのパラメーターがある場合。  
  
## 参照  
 [IDebugAsyncOperation インターフェイス](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)