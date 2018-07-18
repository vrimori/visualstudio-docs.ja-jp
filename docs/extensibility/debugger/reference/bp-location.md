---
title: BP_LOCATION |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_LOCATION
helpviewer_keywords:
- BP_LOCATION union
ms.assetid: ed1e874c-f289-4c31-8b6c-04dde03ad0f5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b73a625e21da8e8ba026df140e437e96bdeb1ff5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107021"
---
# <a name="bplocation"></a>BP_LOCATION
ブレークポイントの位置を指す構造体の型を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _BP_LOCATION {  
   BP_LOCATION_TYPE bpLocationType;  
   union {  
      BP_LOCATION_CODE_FILE_LINE   bplocCodeFileLine;  
      BP_LOCATION_CODE_FUNC_OFFSET bplocCodeFuncOffset;  
      BP_LOCATION_CODE_CONTEXT     bplocCodeContext;  
      BP_LOCATION_CODE_STRING      bplocCodeString;  
      BP_LOCATION_CODE_ADDRESS     bplocCodeAddress;  
      BP_LOCATION_DATA_STRING      bplocDataString;  
      BP_LOCATION_RESOLUTION       bplocResolution;  
      DWORD                        unused;  
   } bpLocation;  
} BP_LOCATION;  
```  
  
```csharp  
public struct BP_LOCATION {  
   public uint   bpLocationType;  
   public IntPtr unionmember1;  
   public IntPtr unionmember2;  
   public IntPtr unionmember3;  
   public IntPtr unionmember4;  
};  
```  
  
## <a name="members"></a>メンバー  
 `bpLocationType`  
 値、 [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md)を解釈するための列挙、`bpLocation`共用体、または`unionmemberX`メンバー。  
  
 `bpLocation`.`bplocCodeFileLine`  
 [C++ のみ]含まれています、 [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)場合構造体`bpLocationType`  = `BPLT_CODE_FILE_LINE`です。  
  
 `bpLocation.bplocCodeFuncOffset`  
 [C++ のみ]含まれています、 [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)場合構造体`bpLocationType`  = `BPLT_CODE_FUNC_OFFSET`です。  
  
 `bpLocation.bplocCodeContext`  
 [C++ のみ]含まれています、 [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)場合構造体`bpLocationType`  = `BPLT_CODE_CONTEXT`です。  
  
 `bpLocation.bplocCodeString`  
 [C++ のみ]含まれています、 [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)場合構造体`bpLocationType`  = `BPLT_CODE_STRING`です。  
  
 `bpLocation.bplocCodeAddress`  
 [C++ のみ]含まれています、 [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)場合構造体`bpLocationType`  = `BPLT_CODE_ADDRESS`です。  
  
 `bpLocation.bplocDataString`  
 [C++ のみ]含まれています、 [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)場合構造体`bpLocationType`  = `BPLT_DATA_STRING`です。  
  
 `bpLocation.bplocResolution`  
 [C++ のみ]含まれています、 [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)場合構造体`bpLocationType`  = `BPLT_RESOLUTION`です。  
  
 `unionmember1`  
 [C# の場合のみ]解釈する方法については、「解説」を参照してください。  
  
 `unionmember2`  
 [C# の場合のみ]解釈する方法については、「解説」を参照してください。  
  
 `unionmember3`  
 [C# の場合のみ]解釈する方法については、「解説」を参照してください。  
  
 `unionmember4`  
 [C# の場合のみ]解釈する方法については、「解説」を参照してください。  
  
## <a name="remarks"></a>コメント  
 この構造体のメンバーである、 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)と[BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)構造体。  
  
 [C# の場合のみ]`unionmemberX`メンバーは、次の表に従って解釈されます。 左の列を確認、`bpLocationType`値から、それぞれを決定するその他の列にわたって確認`unionmemberX`マーシャ リングおよびメンバーを表します、`unionmemberX`それに従っています。 この構造体 (C#) の一部を解釈する方法の例を参照してください。  
  
|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|  
|----------------------|--------------------|--------------------|--------------------|--------------------|  
|`BPLT_CODE_FILE_LINE`|`string` (コンテキスト)|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|-|-|  
|`BPLT_CODE_FUNC_OFFSET`|`string` (コンテキスト)|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|-|-|  
|`BPLT_CODE_CONTEXT`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|  
|`BPLT_CODE_STRING`|`string` (コンテキスト)|`string` (条件式)|-|-|  
|`BPLT_CODE_ADDRESS`|`string` (コンテキスト)|`string` (モジュール URL)|`string` (関数名)|`string` (アドレス)|  
|`BPLT_DATA_STRING`|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|`string` (コンテキスト)|`string` (データ式)|`uint` (要素の数)|  
|`BPLT_RESOLUTION`|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|-|-|-|  
  
## <a name="example"></a>例  
 この例を解釈する方法を示しています、 `BP_LOCATION` c# での構造、`BPLT_DATA_STRING`型です。 この特定の型は、4 つすべてを解釈する方法を示しています。 `unionmemberX` (オブジェクト、文字列、および数) のすべての可能な形式のメンバーです。  
  
```csharp  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(BP_LOCATION bp)  
        {  
            if (bp.bpLocationType == (uint)enum_BP_LOCATION_TYPE.BPLT_DATA_STRING)  
            {  
                 IDebugThread2 pThread = (IDebugThread2)Marshal.GetObjectForIUnknown(bp.unionmember1);  
                 string context = Marshal.PtrToStringBSTR(bp.unionmember2);  
                 string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);  
                 uint numElements = (uint)Marshal.ReadInt32(bp.unionmember4);  
            }  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)   
 [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)   
 [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)   
 [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)   
 [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)   
 [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)   
 [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)