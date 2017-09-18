---
title: "FRAMEINFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FRAMEINFO"
helpviewer_keywords: 
  - "FRAMEINFO 構造体"
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# FRAMEINFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

スタック フレームについて説明します。  
  
## 構文  
  
```cpp#  
typedef struct tagFRAMEINFO {   
   FRAMEINFO_FLAGS    m_dwValidFields;  
   BSTR               m_bstrFuncName;  
   BSTR               m_bstrReturnType;  
   BSTR               m_bstrArgs;  
   BSTR               m_bstrLanguage;  
   BSTR               m_bstrModule;  
   UINT64             m_addrMin;  
   UINT64             m_addrMax;  
   IDebugStackFrame2* m_pFrame;  
   IDebugModule2*     m_pModule;  
   BOOL               m_fHasDebugInfo;  
   BOOL               m_fStaleCode;  
   BOOL               m_fAnnotatedFrame;  
} FRAMEINFO;  
```  
  
```c#  
public struct FRAMEINFO {   
   public uint              m_dwValidFields;  
   public string            m_bstrFuncName;  
   public string            m_bstrReturnType;  
   public string            m_bstrArgs;  
   public string            m_bstrLanguage;  
   public string            m_bstrModule;  
   public ulong             m_addrMin;  
   public ulong             m_addrMax;  
   public IDebugStackFrame2 m_pFrame;  
   public IDebugModule2     m_pModule;  
   public int               m_fHasDebugInfo;  
   public int               m_fStaleCode;  
   public int               m_fAnnotatedFrame;  
} FRAMEINFO;  
```  
  
## メンバー  
 m\_dwValidFields  
 どのフィールドを表示するかを指定する [FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) の列挙体のフラグの組み合わせ。  
  
 m\_bstrFuncName  
 スタック フレームに関連付けられた関数名。  
  
 m\_bstrReturnType  
 スタック フレームに関連付けられた戻り値の型。  
  
 m\_bstrArgs  
 関数の引数はスタック フレームに関連付けられた  
  
 m\_bstrLanguage  
 関数が実行される言語。  
  
 m\_bstrModule  
 スタック フレームに関連付けられているモジュール名。  
  
 m\_addrMin  
 最小限の物理的なスタックのアドレス。  
  
 m\_addrMAX  
 最大物理的なスタックのアドレス。  
  
 m\_pFrame  
 このスタック フレームを表すオブジェクトの [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)。  
  
 m\_pFrame  
 このスタック フレームが含まれているモジュールを表すオブジェクトの [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)。  
  
 m\_fHasDebugInfo  
 デバッグ情報が特定のフレームにある場合は `TRUE`\(\)。  
  
 m\_fHasDebugInfo  
 スタック フレームが有効でないコードに関連付けられている場合以外 `TRUE`\(\)。  
  
 m\_fHasDebugInfo  
 スタック フレームがデバッグ セッションのマネージャー \(SDM\) による注釈が以外の値を返します。`TRUE`\)。  
  
## 解説  
 この構造が表示される [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) のメソッドに渡されます。  この構造体も呼び出しから [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) のメソッドに返される [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) のインターフェイスに含まれるリストに含まれています。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)