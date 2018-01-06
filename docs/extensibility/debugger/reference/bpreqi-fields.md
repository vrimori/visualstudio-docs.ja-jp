---
title: "BPREQI_FIELDS |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BPREQI_FIELDS
helpviewer_keywords: BPREQI_FIELDS enumeration
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1e7c0206ca5834b281447e9a00c4ce3cad0c247c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="bpreqifields"></a>BPREQI_FIELDS
ブレークポイントの要求に関する取得する情報を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
typedef DWORD BPREQI_FIELDS;  
```  
  
```csharp  
public enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
```  
  
## <a name="members"></a>メンバー  
 BPREQI_BPLOCATION  
 初期化/を使用して、 `bpLocation` (ブレークポイントの位置) フィールドの[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)または[BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)構造体。  
  
 BPREQI_LANGUAGE  
 初期化/を使用して、`guidLanguage`のフィールド、`BP_REQUEST_INFO`または`BP_REQUEST_INFO2`構造体。  
  
 BPREQI_PROGRAM  
 初期化/を使用して、`pProgram`のフィールド、`BP_REQUEST_INFO`または`BP_REQUEST_INFO2`構造体。  
  
 BPREQI_PROGRAMNAME  
 初期化/を使用して、`bstrProgramName`のフィールド、`BP_REQUEST_INFO`または`BP_REQUEST_INFO2`構造体。  
  
 BPREQI_THREAD  
 初期化/を使用して、`pThread`のフィールド、`BP_REQUEST_INFO`または`BP_REQUEST_INFO2`構造体。  
  
 BPREQI_THREADNAME  
 初期化/を使用して、`bstrThreadName`のフィールド、`BP_REQUEST_INFO`または`BP_REQUEST_INFO2`構造体。  
  
 BPREQI_PASSCOUNT  
 初期化/を使用して、`bpPassCount`のフィールド、`BP_REQUEST_INFO`または`BP_REQUEST_INFO2`構造体。  
  
 BPREQI_CONDITION  
 初期化/を使用して、 `bpCondition` (ブレークポイントの条件) フィールドの`BP_REQUEST_INFO`または`BP_REQUEST_INFO2`構造体。  
  
 BPREQI_FLAGS  
 初期化/を使用して、`dwFlags`のフィールド、`BP_REQUEST_INFO`または`BP_REQUEST_INFO2`構造体。  
  
 BPREQI_ALLOLDFIELDS  
 すべてのフィールドを使用して初期化の`BP_REQUEST_INFO`構造体。  
  
 BPREQI_VENDOR  
 初期化/を使用して、`guidVendor`フィールド`BP_REQUEST_INFO2`構造体。  
  
 BPREQI_CONSTRAINT  
 初期化/を使用して、`bstrConstraint`フィールド`BP_REQUEST_INFO2`構造体。  
  
 BPREQI_TRACEPOINT  
 初期化/を使用して、`bstrTracepoint`フィールド`BP_REQUEST_INFO2`構造体。  
  
 BPREQI_ALLFIELDS  
 すべてのフィールドを指定します、`BP_REQUEST_INFO2`構造体。  
  
## <a name="remarks"></a>コメント  
 引数として渡される、 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)と[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)のどのフィールドを指定する方法、 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)と[BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)構造体を初期化するのには。  
  
 これらのフラグはのどのフィールドを示すためにも使用、`BP_REQUEST_INFO`と`BP_REQUEST_INFO2`構造は、使用し、有効な各構造体が返されるとします。  
  
 これらの値は、ビットごとと組み合わせること`OR`です。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)