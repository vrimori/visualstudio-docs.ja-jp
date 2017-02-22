---
title: "BPREQI_FIELDS | Microsoft Docs"
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
  - "BPREQI_FIELDS"
helpviewer_keywords: 
  - "BPREQI_FIELDS 列挙型"
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# BPREQI_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

ブレークポイントの要求に関して取得する情報を指定します。  
  
## 構文  
  
```cpp  
enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
typedef DWORD BPREQI_FIELDS;  
```  
  
```c#  
public enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
```  
  
## メンバー  
 BPREQI\_BPLOCATION  
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) または [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) の構造体の `bpLocation` \(ブレークポイントの位置\) フィールドと初期化を使用します。  
  
 BPREQI\_LANGUAGE  
 `BP_REQUEST_INFO` または `BP_REQUEST_INFO2` の構造体の初期化と `guidLanguage` のフィールドを使用します。  
  
 BPREQI\_PROGRAM  
 `BP_REQUEST_INFO` または `BP_REQUEST_INFO2` の構造体の初期化と `pProgram` のフィールドを使用します。  
  
 BPREQI\_PROGRAMNAME  
 `BP_REQUEST_INFO` または `BP_REQUEST_INFO2` の構造体の初期化と `bstrProgramName` のフィールドを使用します。  
  
 BPREQI\_THREAD  
 `BP_REQUEST_INFO` または `BP_REQUEST_INFO2` の構造体の初期化と `pThread` のフィールドを使用します。  
  
 BPREQI\_THREADNAME  
 `BP_REQUEST_INFO` または `BP_REQUEST_INFO2` の構造体の初期化と `bstrThreadName` のフィールドを使用します。  
  
 BPREQI\_PASSCOUNT  
 `BP_REQUEST_INFO` または `BP_REQUEST_INFO2` の構造体の初期化と `bpPassCount` のフィールドを使用します。  
  
 BPREQI\_CONDITION  
 `BP_REQUEST_INFO` または `BP_REQUEST_INFO2` の構造体の `bpCondition` \(ブレークポイント条件\) フィールドと初期化を使用します。  
  
 BPREQI\_FLAGS  
 `BP_REQUEST_INFO` または `BP_REQUEST_INFO2` の構造体の初期化と `dwFlags` のフィールドを使用します。  
  
 BPREQI\_ALLOLDFIELDS  
 `BP_REQUEST_INFO` の構造体のすべてのフィールドと初期化を使用します。  
  
 BPREQI\_VENDOR  
 `BP_REQUEST_INFO2` の構造体の初期化と `guidVendor` のフィールドを使用します。  
  
 BPREQI\_CONSTRAINT  
 `BP_REQUEST_INFO2` の構造体の初期化と `bstrConstraint` のフィールドを使用します。  
  
 BPREQI\_TRACEPOINT  
 `BP_REQUEST_INFO2` の構造体の初期化と `bstrTracepoint` のフィールドを使用します。  
  
 BPREQI\_ALLFIELDS  
 `BP_REQUEST_INFO2` の構造についてすべてのフィールドを指定します。  
  
## 解説  
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) と [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) のフィールドを構成する方法を指定するに [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) と [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) のメソッドに引数として渡されます初期化があります。  
  
 各構造が返されるとこれらのフラグは `BP_REQUEST_INFO` と `BP_REQUEST_INFO2` の構造体のフィールドで使用される有効かを示すために使用されます。  
  
 これらの値はビットごとの `OR` と組み合わせることがあります。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)