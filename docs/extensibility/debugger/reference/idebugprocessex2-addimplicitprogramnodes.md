---
title: "IDebugProcessEx2::AddImplicitProgramNodes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcessEx2::AddImplicitProgramNodes"
helpviewer_keywords: 
  - "IDebugProcessEx2::AddImplicitProgramNodes メソッド"
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcessEx2::AddImplicitProgramNodes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このメソッドはで指定された各デバッグ エンジン \(DE\) のプログラム ノードを追加します。  
  
## 構文  
  
```cpp#  
HRESULT AddImplicitProgramNodes(  
   REFGUID guidLaunchingEngine,  
   GUID*   rgguidSpecificEngines,  
   DWORD   celtSpecificEngines  
);  
```  
  
```c#  
int AddImplicitProgramNodes(  
   ref Guid guidLaunchingEngine,  
   Guid[]   rgguidSpecificEngines,  
   uint     celtSpecificEngines  
);  
```  
  
#### パラメーター  
 `guidLaunchingEngine`  
 \[入力\] プログラムの起動に使用するの `GUID` de\-DE \(および独自のプログラムのノードを追加すると仮定されます\)。  
  
 `rgguidSpecificEngines`  
 \[入力\] プログラムのノードが追加される DEs の `GUID` の配列。  
  
 `celtSpecificEngines`  
 \[入力\] `rgguidSpecificEngines` の配列の `GUID`の数。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 `guidLaunchingEngine`\(\) で指定された [プログラムのノード](../../../extensibility/debugger/program-nodes.md) は独自のプログラムのノードを追加すると仮定されるスタートアップ エンジンを除く\) `rgguidSpecificEngines` に登録された各 de\-DE にプログラムの起動時に追加されます。  
  
## 参照  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)   
 [プログラムのノード](../../../extensibility/debugger/program-nodes.md)