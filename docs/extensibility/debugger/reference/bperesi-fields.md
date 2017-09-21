---
title: "BPERESI_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BPERESI_FIELDS"
helpviewer_keywords: 
  - "BPERESI_FIELDS 列挙型"
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# BPERESI_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

ブレークポイントのエラーの解決方法について取得する情報を指定します。  
  
## 構文  
  
```cpp#  
enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD BPERESI_FIELDS;  
```  
  
```c#  
public enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
```  
  
## メンバー  
 PERESI\_BPRESLOCATION  
 [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) の構造体の `bpResLocation` \(ブレークポイントの解決の位置\) フィールドと初期化を使用します。  
  
 BPERESI\_PROGRAM  
 `BP_ERROR_RESOLUTION_INFO` の構造体の初期化と `pProgram` のフィールドを使用します。  
  
 BPERESI\_THREAD  
 `BP_ERROR_RESOLUTION_INFO` の構造体の初期化と `pThread` のフィールドを使用します。  
  
 BPERESI\_MESSAGE  
 `BP_ERROR_RESOLUTION_INFO` の構造体の初期化と `bstrMessage` のフィールドを使用します。  
  
 BPERESI\_TYPE  
 `BP_ERROR_RESOLUTION_INFO` の構造体の `dwType` \(ブレークポイントの型のフィールドと初期化を使用します。  
  
 BPERESI\_ALLFIELDS  
 `BP_ERROR_RESOLUTION_INFO` の構造体のすべてのフィールドと初期化を使用します。  
  
## 解説  
 [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) の構造体のフィールドが初期化する必要があるかのようにパラメーター [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) のメソッドに渡されます。  
  
 この構造が返されるとこれらの値が `BP_ERROR_RESOLUTION_INFO` の構造体のフィールドで使用される有効かを示すために使用されます。  
  
 これらの値はビットごとの `OR` と組み合わせることがあります。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)