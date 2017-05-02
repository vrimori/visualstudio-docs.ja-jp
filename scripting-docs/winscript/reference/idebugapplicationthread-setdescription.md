---
title: "IDebugApplicationThread::SetDescription | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationThread.SetDescription
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplicationThread::SetDescription"
ms.assetid: 084e5b74-af95-41b4-ae55-01f6f4d22168
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationThread::SetDescription
このスレッドの説明を設定します。  
  
## 構文  
  
```  
HRESULT SetDescription(  
   LPCOLESTR  pstrDescription  
);  
```  
  
#### パラメーター  
 `pstrDescription`  
 \[出力\]このスレッドの説明。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、このスレッドの説明を設定します。  
  
## 参照  
 [IDebugApplicationThread インターフェイス](../../winscript/reference/idebugapplicationthread-interface.md)