---
title: "IEnumRemoteDebugApplicationThreads::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumRemoteDebugApplicationThreads.Clone
apilocation: pdm.dll
helpviewer_keywords: 
  - "IEnumRemoteDebugApplicationThreads::Clone"
ms.assetid: d016e7cf-ae73-48ff-aee7-810222e0b05c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumRemoteDebugApplicationThreads::Clone
現在の列挙状態と同じ状態を格納する列挙子を作成します。  
  
## 構文  
  
```  
HRESULT Clone(  
   IEnumRemoteDebugApplicationThreads**  pperdat  
);  
```  
  
#### パラメーター  
 `pperdat`  
 \[入力\]列挙子の重複する `IEnumRemoteDebugApplicationThreads` のインターフェイスを返します。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、現在の列挙子と同じ状態を含む列挙子を作成します。  
  
## 参照  
 [IEnumRemoteDebugApplicationThreads インターフェイス](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)