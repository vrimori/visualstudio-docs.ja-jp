---
title: EXCEPTION_INFO |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- EXCEPTION_INFO
helpviewer_keywords:
- EXCEPTION_INFO structure
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 557b293579664b5438a1c45f9927fe6833ee43c6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49285312"
---
# <a name="exceptioninfo"></a>EXCEPTION_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

例外またはデバッグ中のプログラムによってスローされた実行時エラーについて説明します。  
  
## <a name="syntax"></a>構文  
  
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
 例外または実行時エラーの識別コード。  
  
 dwState  
 値、 [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)例外の状態を定義する列挙です。  
  
 guidType  
 GUID の言語識別子か、`guidLang`または`guidEng`します。  
  
## <a name="remarks"></a>Remarks  
 この構造体がパラメーターとして渡される、 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)と[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)メソッド。 この構造体に渡されることも、 [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)情報を格納するメソッド。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)   
 [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)

