---
title: "MODULE_INFO_FIELDS | Microsoft Docs"
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
  - "MODULE_INFO_FIELDS"
helpviewer_keywords: 
  - "MODULE_INFO_FIELDS 列挙型"
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# MODULE_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

モジュールのデバッグ情報のフラグを指定します。  
  
## 構文  
  
```cpp#  
enum enum_MODULE_INFO_FIELDS {   
   MIF_NONE              = 0x0000,  
   MIF_NAME              = 0x0001,  
   MIF_URL               = 0x0002,  
   MIF_VERSION           = 0x0004,  
   MIF_DEBUGMESSAGE      = 0x0008,  
   MIF_LOADADDRESS       = 0x0010,  
   MIF_PREFFEREDADDRESS  = 0x0020,  
   MIF_SIZE              = 0x0040,  
   MIF_LOADORDER         = 0x0080,  
   MIF_TIMESTAMP         = 0x0100,  
   MIF_URLSYMBOLLOCATION = 0x0200,  
   MIF_FLAGS             = 0x0400,  
   MIF_ALLFIELDS         = 0x07ff  
};  
typedef DWORD MODULE_INFO_FIELDS;  
```  
  
```c#  
public enum enum_MODULE_INFO_FIELDS {   
   MIF_NONE              = 0x0000,  
   MIF_NAME              = 0x0001,  
   MIF_URL               = 0x0002,  
   MIF_VERSION           = 0x0004,  
   MIF_DEBUGMESSAGE      = 0x0008,  
   MIF_LOADADDRESS       = 0x0010,  
   MIF_PREFFEREDADDRESS  = 0x0020,  
   MIF_SIZE              = 0x0040,  
   MIF_LOADORDER         = 0x0080,  
   MIF_TIMESTAMP         = 0x0100,  
   MIF_URLSYMBOLLOCATION = 0x0200,  
   MIF_FLAGS             = 0x0400,  
   MIF_ALLFIELDS         = 0x07ff  
};  
```  
  
## メンバー  
 MIF\_NONE  
 初期化使用または構造体のフィールドと \[なし\]  
  
 MIF\_NAME  
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) の構造体の初期化と `m_bstrName` のフィールドを使用します。  
  
 MIF\_URL  
 `MODULE_INFO` の構造体の初期化と `m_bstrUrl` のフィールドを使用します。  
  
 MIF\_VERSION  
 `MODULE_INFO` の構造体の初期化と `m_bstrVersion` のフィールドを使用します。  
  
 MIF\_DEBUGMESSAGE  
 `MODULE_INFO` の構造体の初期化と `m_bstrDebugMessage` のフィールドを使用します。  
  
 MIF\_LOADADDRESS  
 `MODULE_INFO` の構造体の初期化と `m_addrLoadAddress` のフィールドを使用します。  
  
 MIF\_PREFFEREDADDRESS  
 `MODULE_INFO` の構造体の初期化と `m_addrPreferredLoadAddress` のフィールドを使用します。  
  
 MIF\_SIZE  
 `MODULE_INFO` の構造体の初期化と `m_dwSize` のフィールドを使用します。  
  
 MIF\_LOADORDER  
 `MODULE_INFO` の構造体の初期化と `m_dwLoadOrder` のフィールドを使用します。  
  
 MIF\_TIMESTAMP  
 `MODULE_INFO` の構造体の初期化と `m_TimeStamp` のフィールドを使用します。  
  
 MIF\_URLSYMBOLLOCATION  
 `MODULE_INFO` の構造体の初期化と `m_bstrUrlSymbolLocation` のフィールドを使用します。  
  
 MIF\_FLAGS  
 `MODULE_INFO` の構造体の初期化と `m_dwModuleFlags` のフィールドを使用します。  
  
 MIF\_ALLFIELDS  
 すべての `MODULE_INFO` 構造体のフィールドの初期化とを使用します。  
  
## 解説  
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) の構造体のフィールドが初期化するかを示すためにこれらの値は引数 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) のメソッドに渡されます。  
  
 `MODULE_INFO` の構造体はこれらの値がどのフィールドが使用され有効かを示すために使用されます。  
  
 これらのフラグはビットごと `OR` に組み合わせることがあります。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)