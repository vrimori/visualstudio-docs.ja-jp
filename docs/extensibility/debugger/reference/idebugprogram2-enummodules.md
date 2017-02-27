---
title: "IDebugProgram2::EnumModules | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::EnumModules"
helpviewer_keywords: 
  - "IDebugProgram2::EnumModules"
ms.assetid: 876ac9da-3b7c-4156-b79a-8f340e9fcea6
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgram2::EnumModules
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このプログラムを読み込む取得し実行しているモジュールのリストを返します。  
  
## 構文  
  
```cpp#  
HRESULT EnumModules(   
   IEnumDebugModules2** ppEnum  
);  
```  
  
```c#  
int EnumModules(   
   out IEnumDebugModules2 ppEnum  
);  
```  
  
#### パラメーター  
 `ppEnum`  
 \[出力\] モジュールの一覧を含む [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) のオブジェクトを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 モジュールはDLL またはアセンブリで  **モジュール** 通常のデバッグ ウィンドウに表示されます。  
  
## 参照  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)