---
title: "EXCEPTION_INFO |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- EXCEPTION_INFO
helpviewer_keywords:
- EXCEPTION_INFO structure
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 6ae273934cc3224a189c94f371fdbe1e3bcc1c68
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="exceptioninfo"></a>EXCEPTION_INFO
例外またはデバッグ中のプログラムによってスローされた実行時エラーについて説明します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct tagEXCEPTION_INFO {   
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   BSTR            bstrExceptionName;  
   DWORD           dwCode;  
   EXCEPTION_STATE dwState;  
   GUID            guidType;  
} EXCEPTION_INFO;  
```  
  
```csharp  
public struct EXCEPTION_INFO {   
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public string         bstrExceptionName;  
   public uint           dwCode;  
   public uint           dwState;  
   public Guid           guidType;  
};  
```  
  
## <a name="members"></a>メンバー  
 pProgram  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)例外が発生したプログラムを表すオブジェクト。  
  
 bstrProgramName  
 例外が発生したプログラムの名前。  
  
 bstrExceptionName  
 例外の名前。  
  
 dwCode  
 例外または実行時エラーの識別コードです。  
  
 dwState  
 値、 [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)例外の状態を定義する列挙値。  
  
 guidType  
 GUID の言語識別子か、`guidLang`または`guidEng`です。  
  
## <a name="remarks"></a>コメント  
 この構造体がパラメーターとして渡される、 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)と[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)メソッドです。 この構造体に渡されます、 [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)格納するメソッド。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)   
 [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)