---
title: BP_LOCATION |Microsoft Docs
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
- BP_LOCATION
helpviewer_keywords:
- BP_LOCATION union
ms.assetid: ed1e874c-f289-4c31-8b6c-04dde03ad0f5
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6e154fe6b1121855e50c32b342c3c11566cbcd03
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749109"
---
# <a name="bplocation"></a>BP_LOCATION
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

ブレークポイントの位置を記述するために使用する構造体の型を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 [C++ のみ]含まれています、 [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)場合構造体`bpLocationType`  = `BPLT_CODE_FILE_LINE`します。  
  
 `bpLocation.bplocCodeFuncOffset`  
 [C++ のみ]含まれています、 [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)場合構造体`bpLocationType`  = `BPLT_CODE_FUNC_OFFSET`します。  
  
 `bpLocation.bplocCodeContext`  
 [C++ のみ]含まれています、 [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)場合構造体`bpLocationType`  = `BPLT_CODE_CONTEXT`します。  
  
 `bpLocation.bplocCodeString`  
 [C++ のみ]含まれています、 [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)場合構造体`bpLocationType`  = `BPLT_CODE_STRING`します。  
  
 `bpLocation.bplocCodeAddress`  
 [C++ のみ]含まれています、 [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)場合構造体`bpLocationType`  = `BPLT_CODE_ADDRESS`します。  
  
 `bpLocation.bplocDataString`  
 [C++ のみ]含まれています、 [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)場合構造体`bpLocationType`  = `BPLT_DATA_STRING`します。  
  
 `bpLocation.bplocResolution`  
 [C++ のみ]含まれています、 [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)場合構造体`bpLocationType`  = `BPLT_RESOLUTION`します。  
  
 `unionmember1`  
 [C#のみ]解釈する方法については、「解説」を参照してください。  
  
 `unionmember2`  
 [C#のみ]解釈する方法については、「解説」を参照してください。  
  
 `unionmember3`  
 [C#のみ]解釈する方法については、「解説」を参照してください。  
  
 `unionmember4`  
 [C#のみ]解釈する方法については、「解説」を参照してください。  
  
## <a name="remarks"></a>Remarks  
 この構造体のメンバーである、 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)と[BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)構造体。  
  
 [C#のみ]`unionmemberX`メンバーは、次の表に従って解釈されます。 左の列を確認、`bpLocationType`値、それぞれを決定するその他の列の間で外観`unionmemberX`マーシャ リングおよびメンバーを表します、`unionmemberX`それに応じて。 この構造体 (C#) の一部を解釈する方法の例を参照してください。  
  
|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|  
|----------------------|--------------------|--------------------|--------------------|--------------------|  
|`BPLT_CODE_FILE_LINE`|`string` (コンテキスト)|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|-|-|  
|`BPLT_CODE_FUNC_OFFSET`|`string` (コンテキスト)|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|-|-|  
|`BPLT_CODE_CONTEXT`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|  
|`BPLT_CODE_STRING`|`string` (コンテキスト)|`string` (条件式)|-|-|  
|`BPLT_CODE_ADDRESS`|`string` (コンテキスト)|`string` (モジュールの URL)|`string` (関数名)|`string` (アドレス)|  
|`BPLT_DATA_STRING`|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|`string` (コンテキスト)|`string` (データ式)|`uint` (要素の数)|  
|`BPLT_RESOLUTION`|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|-|-|-|  
  
## <a name="example"></a>例  
 この例を解釈する方法を示しています、 `BP_LOCATION` c# の構造、`BPLT_DATA_STRING`型。 この特定の型は、4 つすべてを解釈する方法を示しています。 `unionmemberX` (オブジェクト、文字列、および数) のすべての可能な形式のメンバー。  
  
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
  
## <a name="requirements"></a>必要条件  
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

