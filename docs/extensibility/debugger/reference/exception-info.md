---
title: "EXCEPTION_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EXCEPTION_INFO"
helpviewer_keywords: 
  - "EXCEPTION_INFO 構造体"
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# EXCEPTION_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

デバッグするプログラムによってスローされる例外または実行時エラーについて説明します。  
  
## 構文  
  
```cpp#  
typedef struct tagEXCEPTION_INFO {   
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   BSTR            bstrExceptionName;  
   DWORD           dwCode;  
   EXCEPTION_STATE dwState;  
   GUID            guidType;  
} EXCEPTION_INFO;  
```  
  
```c#  
public struct EXCEPTION_INFO {   
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public string         bstrExceptionName;  
   public uint           dwCode;  
   public uint           dwState;  
   public Guid           guidType;  
};  
```  
  
## メンバー  
 pProgram  
 例外が発生した [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) プログラムを表すオブジェクト。  
  
 bstrProgramName  
 例外が発生したプログラムの名前。  
  
 bstrExceptionName  
 例外の名前。  
  
 dwCode  
 例外や実行時エラー コードの ID。  
  
 dwState  
 例外の状態を定義する [EXCEPTION\_STATE](../../../extensibility/debugger/reference/exception-state.md) の列挙体の値。  
  
 guidType  
 GUID の言語識別子 `guidLang`または `guidEng`。  
  
## 解説  
 この構造は [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) と [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) のメソッドにパラメーターとして渡します。  この構造体には入力される [GetException](../Topic/IDebugExceptionEvent2::GetException.md) のメソッドに渡されます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [EXCEPTION\_STATE](../../../extensibility/debugger/reference/exception-state.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)   
 [GetException](../Topic/IDebugExceptionEvent2::GetException.md)