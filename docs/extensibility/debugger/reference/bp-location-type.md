---
title: "BP_LOCATION_TYPE | Microsoft Docs"
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
  - "BP_LOCATION_TYPE"
helpviewer_keywords: 
  - "BP_LOCATION_TYPE 構造体"
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_LOCATION_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

ブレークポイントの要求に対してブレークポイントの場所の種類を指定します。  
  
## 構文  
  
```cpp#  
enum enum_BP_LOCATION_TYPE {   
   BPLT_NONE               = 0x00000000,  
   BPLT_FILE_LINE          = 0x00010000,  
   BPLT_FUNC_OFFSET        = 0x00020000,  
   BPLT_CONTEXT            = 0x00030000,  
   BPLT_STRING             = 0x00040000,  
   BPLT_ADDRESS            = 0x00050000,  
   BPLT_RESOLUTION         = 0x00060000,  
   BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,  
   BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,  
   BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,  
   BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,  
   BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,  
   BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,  
   BPLT_TYPE_MASK          = 0x0000FFFF,  
   BPLT_LOCATION_TYPE_MASK = 0xFFFF0000  
};  
typedef DWORD BP_LOCATION_TYPE;  
```  
  
```c#  
public enum enum_BP_LOCATION_TYPE {   
   BPLT_NONE               = 0x00000000,  
   BPLT_FILE_LINE          = 0x00010000,  
   BPLT_FUNC_OFFSET        = 0x00020000,  
   BPLT_CONTEXT            = 0x00030000,  
   BPLT_STRING             = 0x00040000,  
   BPLT_ADDRESS            = 0x00050000,  
   BPLT_RESOLUTION         = 0x00060000,  
   BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,  
   BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,  
   BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,  
   BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,  
   BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,  
   BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,  
   BPLT_TYPE_MASK          = 0x0000FFFF,  
   BPLT_LOCATION_TYPE_MASK = 0xFFFF0000  
};  
```  
  
## メンバー  
 BPLT\_NONE  
 ブレークポイントの位置を指定しません。  
  
 BPLT\_FILE\_LINE  
 ブレークポイントの場所の種類にファイルの行指定します。  
  
 BPLT\_FUNC\_OFFSET  
 ブレークポイントの場所の種類関数のオフセットを指定します。  
  
 BPLT\_CONTEXT  
 コンテキストとしてブレークポイントの場所の種類を指定します。  
  
 BPLT\_STRING  
 文字列としてブレークポイントの場所の種類を指定します。  
  
 BPLT\_ADDRESS  
 アドレスとしてブレークポイントの場所の種類を指定します。  
  
 BPLT\_RESOLUTION  
 解決としてブレークポイントの場所の種類を指定します。  
  
 BPLT\_CODE\_FILE\_LINE  
 ソース・コード行としてブレークポイントの場所の種類を指定します。  
  
 BPLT\_CODE\_FUNC\_OFFSET  
 ブレークポイントの場所の種類は関数コードのオフセットを指定します。  
  
 BPLT\_CODE\_CONTEXT  
 コード コンテキストとしてブレークポイントの場所の種類を指定します。  
  
 BPLT\_CODE\_STRING  
 コードの文字列としてブレークポイントの場所の種類を指定します。  
  
 BPLT\_CODE\_ADDRESS  
 コード アドレスとしてブレークポイントの場所の種類を指定します。  
  
 BPLT\_DATA\_STRING  
 ブレークポイントの場所の種類にデータの文字列を指定します。  
  
 BPLT\_TYPE\_MASK  
 ブレークポイントの型から値を抽出できるようにビット マスクを指定します。  
  
 BPLT\_LOCATION\_TYPE\_MASK  
 ブレークポイントの位置の型から値を抽出できるようにビット マスクを指定します。  
  
## 解説  
 [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md) のパラメーターとしてメソッドに渡されます。  
  
 ブレークポイントの位置の型はブレークポイントの種類と場所の種類で構成されます。  これはブレークポイントの位置の型はブレークポイントの型 \(たとえば\)`BPT_CODE` または場所の種類 \(`BPLT_FILE_LINE`\) ではないことを示します。  現在サポートされているこの列挙型 \(`BPLT_DATA_STRING` して `BPLT_CODE_FILE_LINE`\) にすべてのブレークポイント位置の種類の定義済み定数が含まれます。  
  
 `BPT_CODE` および `BPT_DATA` は、[BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md) 列挙体のメンバーです。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)   
 [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md)