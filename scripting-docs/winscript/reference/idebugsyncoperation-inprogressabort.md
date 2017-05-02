---
title: "IDebugSyncOperation::InProgressAbort | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugSyncOperation.InProgressAbort
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugSyncOperation::InProgressAbort"
ms.assetid: bfd0889c-b627-4843-b1c6-b6b918f42d61
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSyncOperation::InProgressAbort
別のスレッドで実行中の操作をキャンセルします。  
  
## 構文  
  
```  
HRESULT InProgressAbort();  
```  
  
#### パラメーター  
 このメソッドは、パラメーターを受け取りません。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
|`E_NOTIMPL`|操作をキャンセルできません。|  
|`E_ABORT`|操作を完了できませんでした。|  
  
## 解説  
 プロセス デバッグ マネージャーは別のスレッドで実行中の操作をキャンセルするために、デバッガーのスレッドからのこのメソッドを呼び出します。  
  
 `InProgressAbort` のメソッドが操作を完了できない場合 `E_ABORT` をできるだけ早く返します。  このメソッドは、操作のキャンセルできない場合 `E_NOTIMPL` を返すことができます。  
  
## 参照  
 [IDebugSyncOperation インターフェイス](../../winscript/reference/idebugsyncoperation-interface.md)