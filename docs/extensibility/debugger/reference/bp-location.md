---
title: "BP_LOCATION | Microsoft Docs"
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
  - "BP_LOCATION"
helpviewer_keywords: 
  - "BP_LOCATION 共用体"
ms.assetid: ed1e874c-f289-4c31-8b6c-04dde03ad0f5
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_LOCATION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

ブレークポイントの位置を表すために使用される構成要素の型を指定します。  
  
## 構文  
  
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
  
```c#  
public struct BP_LOCATION {  
   public uint   bpLocationType;  
   public IntPtr unionmember1;  
   public IntPtr unionmember2;  
   public IntPtr unionmember3;  
   public IntPtr unionmember4;  
};  
```  
  
## メンバー  
 `bpLocationType`  
 `bpLocation` の `unionmemberX` または共用体のメンバーを解釈する [BP\_LOCATION\_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) の列挙体の値。  
  
 `bpLocation`.`bplocCodeFileLine`  
 \[C\+\+\] [BP\_LOCATION\_CODE\_FILE\_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) のみの構造を `bpLocationType` \= `bpLocationType``bpLocationType``BPLT_CODE_FILE_LINE` 含まれています。  
  
 `bpLocation.bplocCodeFuncOffset`  
 \[C\+\+\] [BP\_LOCATION\_CODE\_FUNC\_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) のみの構造を `bpLocationType` \= `bpLocationType``bpLocationType``BPLT_CODE_FUNC_OFFSET` 含まれています。  
  
 `bpLocation.bplocCodeContext`  
 \[C\+\+\] [BP\_LOCATION\_CODE\_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) のみの構造を `bpLocationType` \= `bpLocationType``bpLocationType``BPLT_CODE_CONTEXT` 含まれています。  
  
 `bpLocation.bplocCodeString`  
 \[C\+\+\] [BP\_LOCATION\_CODE\_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) のみの構造を `bpLocationType` \= `bpLocationType``bpLocationType``BPLT_CODE_STRING` 含まれています。  
  
 `bpLocation.bplocCodeAddress`  
 \[C\+\+\] [BP\_LOCATION\_CODE\_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) のみの構造を `bpLocationType` \= `bpLocationType``bpLocationType``BPLT_CODE_ADDRESS` 含まれています。  
  
 `bpLocation.bplocDataString`  
 \[C\+\+\] [BP\_LOCATION\_DATA\_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) のみの構造を `bpLocationType` \= `bpLocationType``bpLocationType``BPLT_DATA_STRING` 含まれています。  
  
 `bpLocation.bplocResolution`  
 \[C\+\+\] [BP\_LOCATION\_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) のみの構造を `bpLocationType` \= `bpLocationType``bpLocationType``BPLT_RESOLUTION` 含まれています。  
  
 `unionmember1`  
 \[C\#\] を解釈する方法の解説を参照してください。  
  
 `unionmember2`  
 \[C\#\] を解釈する方法の解説を参照してください。  
  
 `unionmember3`  
 \[C\#\] を解釈する方法の解説を参照してください。  
  
 `unionmember4`  
 \[C\#\] を解釈する方法の解説を参照してください。  
  
## 解説  
 この構造は [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) と [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) の構造体のメンバーです。  
  
 \[C\#\] `unionmemberX` のみのメンバーを次の表に従って解釈されます。  `unionmemberX` の各メンバーが表す `unionmemberX` を確認しそれに応じてマーシャリングします。を確認するには左の列で他の列間で `bpLocationType` の値と外観を示します。  C\# でこの構造の一部を解釈する方法の例を参照してください。  
  
|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|  
|----------------------|--------------------|--------------------|--------------------|--------------------|  
|`BPLT_CODE_FILE_LINE`|`string` コンテキスト \(\)|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|\-|\-|  
|`BPLT_CODE_FUNC_OFFSET`|`string` コンテキスト \(\)|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|\-|\-|  
|`BPLT_CODE_CONTEXT`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|\-|\-|\-|  
|`BPLT_CODE_STRING`|`string` コンテキスト \(\)|`string` 条件式 \(\)|\-|\-|  
|`BPLT_CODE_ADDRESS`|`string` コンテキスト \(\)|`string` \(モジュールの URL\)|`string` \(関数名\)|`string` アドレス \(\)|  
|`BPLT_DATA_STRING`|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|`string` コンテキスト \(\)|`string` データ \(式\)|`uint` \(要素数\)|  
|`BPLT_RESOLUTION`|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|\-|\-|\-|  
  
## 使用例  
 この例で `BPLT_DATA_STRING` の型に対して C\# `BP_LOCATION` の構造を解釈する方法を示します。  この特定の型では使用可能な形式 \(オブジェクトでブール型文字列数値\) の `unionmemberX` のすべてのメンバーが 4 つ解釈する方法を示します。  
  
```c#  
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
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_LOCATION\_CODE\_FILE\_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)   
 [BP\_LOCATION\_CODE\_FUNC\_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)   
 [BP\_LOCATION\_CODE\_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)   
 [BP\_LOCATION\_CODE\_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)   
 [BP\_LOCATION\_CODE\_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)   
 [BP\_LOCATION\_DATA\_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)   
 [BP\_LOCATION\_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)