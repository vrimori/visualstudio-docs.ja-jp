---
title: "IDebugProgramEngines2::EnumPossibleEngines | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramEngines2::EnumPossibleEngines"
helpviewer_keywords: 
  - "IDebugProgramEngines2::EnumPossibleEngines"
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgramEngines2::EnumPossibleEngines
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このプログラムをデバッグできるすべての可能なデバッグ エンジン \(DE\) の GUID を返します。  
  
## 構文  
  
```cpp#  
HRESULT EnumPossibleEngines(   
   DWORD  celtBuffer,  
   GUID*  rgguidEngines,  
   DWORD* pceltEngines  
);  
```  
  
```c#  
int EnumPossibleEngines(   
   uint      celtBuffer,  
   GUID[]    rgguidEngines,  
   ref DWORD pceltEngines  
);  
```  
  
#### パラメーター  
 `celtBuffer`  
 \[出力\] 返されるします GUIDs の数。  これは`rgguidEngines` の配列の最大サイズを指定します。  
  
 `rgguidEngines`  
 \[入力出力\] 入力されるします GUIDs の配列。  
  
 `pceltEngines`  
 \[入力\] します GUIDs の実際の数を返す返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  バッファーのサイズが十分な大きさは `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` \[C\+\+\] または \[C\#\] 0x8007007A。  
  
## 解説  
 多くの場合エンジンは一度に 0 `celtBuffer` 場合パラメーターの設定および NULL 値に `rgguidEngines` のパラメーターをに設定してこのメソッドを呼び出すかを確認します。  これは `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` \(C\# の場合\) 0x8007007A を返し`pceltEngines` のパラメーターが必要なバッファーのサイズを返します。  
  
## 参照  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)