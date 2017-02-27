---
title: "BP_ERROR_RESOLUTION_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_ERROR_RESOLUTION_INFO"
helpviewer_keywords: 
  - "BP_ERROR_RESOLUTION_INFO 構造体"
ms.assetid: a6b83242-5728-4716-80f3-840c96d59c6c
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# BP_ERROR_RESOLUTION_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

位置およびプログラムのブレークポイントを含むスレッド エラーの解決方法について説明します。  
  
## 構文  
  
```cpp#  
typedef struct _BP_ERROR_RESOLUTION_INFO {   
   BPERESI_FIELDS         dwFields;  
   BP_RESOLUTION_LOCATION bpResLocation;  
   IDebugProgram2*        pProgram;  
   IDebugThread2*         pThread;  
   BSTR                   bstrMessage;  
   BP_ERROR_TYPE          dwType;  
} BP_ERROR_RESOLUTION_INFO;  
```  
  
```c#  
public struct BP_ERROR_RESOLUTION_INFO {   
   public uint                   dwFields;  
   public BP_RESOLUTION_LOCATION bpResLocation;  
   public IDebugProgram2         pProgram;  
   public IDebugThread2          pThread;  
   public string                 bstrMessage;  
   public uint                   dwType;  
};  
```  
  
## メンバー  
 `dwFields`  
 [BPERESI\_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) の列挙型でこの構造体のフィールドが設定されるかを指定の値の組み合わせ。  
  
 `bpResLocation`  
 ブレークポイントの解決の場所を指定する [BP\_RESOLUTION\_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) の和集合。  
  
 `pProgram`  
 ブレークポイントのエラーが発生したアプリケーション [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) を表すオブジェクト。  
  
 `pThread`  
 ブレークポイントのエラーが発生したアプリケーション スレッドを表すオブジェクトの [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) を実行します。  
  
 `bstrMessage`  
 文字列警告またはエラー メッセージこのエラーの解決になります。  
  
 `dwType`  
 ブレークポイントのエラー [BP\_ERROR\_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) の種類を指定する列挙体の値。  
  
## 解説  
 この構造は [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) のメソッドから返されます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)   
 [BPRESI\_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)   
 [BP\_RESOLUTION\_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP\_ERROR\_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)