---
title: BPREQI_FIELDS90 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BPREQI_FIELDS90 enumeration
ms.assetid: bf6f7efc-39f2-46a2-906d-c3647bf89995
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1ce9ca3251faf79ea87863e78d039dde722f5961
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908847"
---
# <a name="bpreqifields90"></a>BPREQI_FIELDS90
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

取得するブレークポイントの要求についての情報を指定する有効な値を列挙します。 この列挙体を拡張、 [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)列挙体。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
enum enum_BPREQI_FIELDS90  
{  
   // VS 8.0 values  
   BPREQI90_BPLOCATION                = 0x0001,  
   BPREQI90_LANGUAGE                  = 0x0002,  
   BPREQI90_PROGRAM                   = 0x0004,  
   BPREQI90_PROGRAMNAME               = 0x0008,  
   BPREQI90_THREAD                    = 0x0010,  
   BPREQI90_THREADNAME                = 0x0020,  
   BPREQI90_PASSCOUNT                 = 0x0040,  
   BPREQI90_CONDITION                 = 0x0080,  
   BPREQI90_FLAGS                     = 0x0100,  
   BPREQI90_ALLOLDFIELDS              = 0x01ff,  
   BPREQI90_VENDOR                    = 0x0200,  
   BPREQI90_CONSTRAINT                = 0x0400,  
   BPREQI90_TRACEPOINT                = 0x0800,  
  
   // Values added in VS 9.0  
   BPREQI90_MACROTRACEPOINT           = 0x1000,  
  
   BPREQI90_ALLFIELDS                 = 0xffff  
};  
typedef DWORD BPREQI_FIELDS90;  
```  
  
```csharp  
public enum enum_BPREQI_FIELDS90  
{  
    // VS 8.0 values  
    BPREQI90_BPLOCATION                = 0x0001,  
    BPREQI90_LANGUAGE                  = 0x0002,  
    BPREQI90_PROGRAM                   = 0x0004,  
    BPREQI90_PROGRAMNAME               = 0x0008,  
    BPREQI90_THREAD                    = 0x0010,  
    BPREQI90_THREADNAME                = 0x0020,  
    BPREQI90_PASSCOUNT                 = 0x0040,  
    BPREQI90_CONDITION                 = 0x0080,  
    BPREQI90_FLAGS                     = 0x0100,  
    BPREQI90_ALLOLDFIELDS              = 0x01ff,  
    BPREQI90_VENDOR                    = 0x0200,  
    BPREQI90_CONSTRAINT                = 0x0400,  
    BPREQI90_TRACEPOINT                = 0x0800,  
  
    // Values added in VS 9.0  
    BPREQI90_MACROTRACEPOINT           = 0x1000,  
  
    BPREQI90_ALLFIELDS                 = 0xffff  
};  
```  
  
#### <a name="parameters"></a>パラメーター  
 BPREQI90_BPLOCATION  
 初期化または使用して、 `bpLocation` (ブレークポイントの位置) フィールドの[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)または[BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)構造体。  
  
 BPREQI90_LANGUAGE  
 初期化または使用して、`guidLanguage`のフィールド、`BP_REQUEST_INFO`または`BP_REQUEST_INFO2`構造体。  
  
 BPREQI90_PROGRAM  
 初期化または使用して、`pProgram`のフィールド、`BP_REQUEST_INFO`または`BP_REQUEST_INFO2`構造体。  
  
 BPREQI90_PROGRAMNAME  
 初期化または使用して、`bstrProgramName`のフィールド、`BP_REQUEST_INFO`または`BP_REQUEST_INFO2`構造体。  
  
 BPREQI90_THREAD  
 初期化または使用して、`pThread`のフィールド、`BP_REQUEST_INFO`または`BP_REQUEST_INFO2`構造体。  
  
 BPREQI90_THREADNAME  
 初期化または使用して、`bstrThreadName`のフィールド、`BP_REQUEST_INFO`または`BP_REQUEST_INFO2`構造体。  
  
 BPREQI90_PASSCOUNT  
 初期化または使用して、`bpPassCount`のフィールド、`BP_REQUEST_INFO`または`BP_REQUEST_INFO2`構造体。  
  
 BPREQI90_CONDITION  
 初期化または使用して、 `bpCondition` (ブレークポイント条件) フィールドの`BP_REQUEST_INFO`または`BP_REQUEST_INFO2`構造体。  
  
 BPREQI90_FLAGS  
 初期化または使用して、`dwFlags`のフィールド、`BP_REQUEST_INFO`または`BP_REQUEST_INFO2`構造体。  
  
 BPREQI90_ALLOLDFIELDS  
 初期化またはすべてのフィールドを使用して、、`BP_REQUEST_INFO`構造体。  
  
 BPREQI90_VENDOR  
 初期化または使用して、`guidVendor`フィールド`BP_REQUEST_INFO2`構造体。  
  
 BPREQI90_CONSTRAINT  
 初期化または使用して、`bstrConstraint`フィールド`BP_REQUEST_INFO2`構造体。  
  
 BPREQI90_TRACEPOINT  
 初期化または使用して、`bstrTracepoint`フィールド`BP_REQUEST_INFO2`構造体。  
  
 BPREQI90_MACROTRACEPOINT  
 初期化または使用して、`bstrMacroTracepoint`フィールド`BP_REQUEST_INFO2`構造体。 BPREQI_ALLFIELDS では、このフィールドは含まれません。  
  
 BPREQI90_ALLFIELDS  
 すべてのフィールドを指定します、`BP_REQUEST_INFO2`構造体。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: Msdbg90.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

