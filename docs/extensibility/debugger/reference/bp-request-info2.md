---
title: "BP_REQUEST_INFO2 | Microsoft Docs"
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
  - "BP_REQUEST_INFO2"
helpviewer_keywords: 
  - "BP_REQUEST_INFO2 構造体"
ms.assetid: 008c87f7-a76e-43d3-8904-11b225d6a9a5
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_REQUEST_INFO2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

販売元の GUID制約トレース ポイントを含むブレークポイントを実装するために必要な情報が含まれています。  
  
## 構文  
  
```cpp#  
typedef struct _BP_REQUEST_INFO2 {  
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
   GUID            guidVendor;  
   BSTR            bstrConstraint;  
   BSTR            bstrTracepoint;  
} BP_REQUEST_INFO2;  
```  
  
```c#  
public struct BP_REQUEST_INFO2 {  
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
   public Guid           guidVendor;  
   public string         bstrConstraint;  
   public string         bstrTracepoint;  
};  
```  
  
## メンバー  
 `dwFields`  
 どのフィールドを表示するかを指定する [BPREQI\_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) の列挙体のフラグの組み合わせ。  
  
 `guidLanguage`  
 言語の GUID。  
  
 `bpLocation`  
 ブレークポイントの位置の種類を指定する [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) の構造体。  
  
 `pProgram`  
 ブレークポイントが発生したアプリケーション [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) を表すオブジェクト。  
  
 `bstrProgramName`  
 ブレークポイントが発生するアプリケーションの名前。  
  
 `pThread`  
 ブレークポイントが発生したスレッドを表す [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) のオブジェクト。  
  
 `bstrThreadName`  
 ブレークポイントが発生したスレッドの名前。  
  
 `bpCondition`  
 ブレークポイントが発生する条件を示す [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) の構造体。  
  
 `bpPassCount`  
 ブレークポイントのパスの数の情報を含む [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) の構造体。  
  
 `dwFlags`  
 要求されたブレークポイントのフラグを指定する [BP\_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) の列挙体のフラグの組み合わせ。  
  
 `guidVendor`  
 販売元の GUID。  null 値を指定できます。  
  
 `bstrConstraint`  
 ブレークポイントの制約の名前。  null 値を指定できます。  
  
 `bstrTracepoint`  
 トレースのポイントの名前。  null 値を指定できます。  
  
## 解説  
 この構造は [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md) のメソッドによって返されます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)   
 [BPREQI\_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP\_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)