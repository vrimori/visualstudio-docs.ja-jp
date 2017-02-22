---
title: "CONTEXT_INFO_FIELDS | Microsoft Docs"
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
  - "CONTEXT_INFO_FIELDS"
helpviewer_keywords: 
  - "CONTEXT_INFO_FIELDS 列挙型"
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# CONTEXT_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

メモリのコンテキストに関して取得する情報を指定します。  
  
## 構文  
  
```cpp#  
enum enum_CONTEXT_INFO_FIELDS {   
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
typedef DWORD CONTEXT_INFO_FIELDS;  
```  
  
```c#  
public enum enum_CONTEXT_INFO_FIELDS {  
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
```  
  
## メンバー  
 CIF\_MODULEURL  
 [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md) の構造体の初期化と `bstrModuleUrl` のフィールドを使用します。  
  
 CIF\_FUNCTION  
 `CONTEXT_INFO` の構造体の初期化と `bstrFunction` のフィールドを使用します。  
  
 CIF\_FUNCTIONOFFSET  
 `CONTEXT_INFO` の構造体の初期化と `posFunctionOffset` のフィールドを使用します。  
  
 CIF\_ADDRESS  
 `CONTEXT_INFO` の構造体の初期化と `bstrAddress` のフィールドを使用します。  
  
 CIF\_ADDRESSOFFSET  
 `CONTEXT_INFO` の構造体の初期化と `bstrAddressOffset` のフィールドを使用します。  
  
 CIF\_ALLFIELDS  
 `CONTEXT_INFO` の構造体のすべてのフィールドと初期化を使用します。  
  
## 解説  
 これらの値は [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md) の構造体のフィールドが初期化するかを示す [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) のメソッドのパラメーターに渡されます。  
  
 構造体が返されるとこれらのフラグは `CONTEXT_INFO` の構造体のフィールドで使用される有効かを示すために使用されます。  
  
 これらの値はまたはこれらのビットごとに組み合わせることがあります。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)