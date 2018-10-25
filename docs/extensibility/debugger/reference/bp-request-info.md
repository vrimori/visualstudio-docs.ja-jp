---
title: BP_REQUEST_INFO |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_REQUEST_INFO
helpviewer_keywords:
- BP_REQUEST_INFO structure
ms.assetid: 42a31412-5b6b-47fe-a762-0c2bc769e1cc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cf2138a96245e46057fb8ca4bca73b7146a48318
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49877777"
---
# <a name="bprequestinfo"></a>BP_REQUEST_INFO
ブレークポイントを実装するために必要な情報が含まれています。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _BP_REQUEST_INFO {  
   BPREQI_FIELDS   dwFields;  
   GUID            guidLanguage;  
   BP_LOCATION     bpLocation;  
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   IDebugThread2*  pThread;  
   BSTR            bstrThreadName;  
   BP_CONDITION    bpCondition;  
   BP_PASSCOUNT    bpPassCount;  
   BP_FLAGS        dwFlags;  
} BP_REQUEST_INFO;  
```  
  
```csharp  
public struct BP_REQUEST_INFO {  
   public uint           dwFields;  
   public Guid           guidLanguage;  
   public BP_LOCATION    bpLocation;  
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public IDebugThread2  pThread;  
   public string         bstrThreadName;  
   public BP_CONDITION   bpCondition;  
   public BP_PASSCOUNT   bpPassCount;  
   public uint           dwFlags;  
};  
```  
  
## <a name="members"></a>メンバー  
 `dwFields`  
 フラグの組み合わせ、 [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)フィールドが記入を指定する列挙体。  
  
 `guidLanguage`  
 言語の GUID。  
  
 `bpLocation`  
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)ブレークポイントの場所の種類を指定する構造体。  
  
 `pProgram`  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)ブレークポイントが発生したアプリケーションを表すオブジェクト。  
  
 `bstrProgramName`  
 ブレークポイントが発生したアプリケーションの名前。  
  
 `pThread`  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)ブレークポイントが発生したスレッドを表すオブジェクト。  
  
 `bstrThreadName`  
 ブレークポイントが発生したスレッドの名前。  
  
 `bpCondition`  
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)ブレークポイントが発生する条件を記述する構造体。  
  
 `bpPassCount`  
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)ブレークポイントのパスの行数の情報を含む構造体。  
  
 `dwFlags`  
 フラグの組み合わせ、 [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)要求されたブレークポイントのフラグを指定する列挙体。  
  
## <a name="remarks"></a>Remarks  
 この構造体がによって返される、 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)メソッド。  
  
 デバッグ エンジン ベンダーの GUID を取得する必要がある場合、ブレークポイント制約またはトレース ポイントを参照してください、 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)構造体。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)