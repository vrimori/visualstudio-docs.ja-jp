---
title: "CODE_PATH | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CODE_PATH"
helpviewer_keywords: 
  - "CODE_PATH 構造体"
ms.assetid: 2d4b2890-4c9d-47e1-83c0-df9c6436427f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# CODE_PATH
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

メソッドまたは関数呼び出しについて説明します。  
  
## 構文  
  
```cpp#  
typedef struct tagCODE_PATH {   
   BSTR                bstrName;  
   IDebugCodeContext2* pCode;  
} CODE_PATH;  
```  
  
```c#  
public struct CODE_PATH {  
   public string            bstrName;  
   public IDebugCodeContext pCode;  
}  
```  
  
## メンバー  
 bstrName  
 コード パス名。  
  
 pCode  
 コード内の関数にステップ インするには[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 識別するオブジェクト。  
  
## 解説  
 この構造体を関数にステップを実行するために使用されます。  [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) でプログラムの現在位置からすべての呼び出しを返します。  この構造は1 種類のこのような呼び出しを表します。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)