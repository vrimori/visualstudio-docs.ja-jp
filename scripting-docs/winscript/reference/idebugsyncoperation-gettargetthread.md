---
title: "IDebugSyncOperation::GetTargetThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugSyncOperation.GetTargetThread
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugSyncOperation::GetTargetThread"
ms.assetid: e6eeeb90-b5ed-4727-8434-fa3186c25013
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSyncOperation::GetTargetThread
この同期操作のターゲット アプリケーションのスレッドを返します。  
  
## 構文  
  
```  
HRESULT GetTargetThread(  
   IDebugApplicationThread**  ppatTarget  
);  
```  
  
#### パラメーター  
 `ppatTarget`  
 \[出力\]この同期操作のターゲット アプリケーションのスレッド。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、同期操作のターゲット アプリケーションのスレッドを返します。  
  
## 参照  
 [IDebugSyncOperation インターフェイス](../../winscript/reference/idebugsyncoperation-interface.md)