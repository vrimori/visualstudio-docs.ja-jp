---
title: "DEBUGREF_INFO_FLAGS | Microsoft Docs"
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
  - "DEBUGREF_INFO_FLAGS"
helpviewer_keywords: 
  - "DEBUGREF_INFO_FLAGS 列挙型"
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# DEBUGREF_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

デバッグの参照オブジェクトに関して取得する情報を指定します。  
  
## 構文  
  
```cpp#  
enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
typedef DWORD DEBUGREF_INFO_FLAGS;  
```  
  
```c#  
public enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
```  
  
## メンバー  
 DEBUGREF\_INFO\_NAME  
 構造体の初期化と `bstrName` のフィールドを使用します。  
  
 DEBUGREF\_INFO\_TYPE  
 構造体の初期化と `bstrType` のフィールドを使用します。  
  
 DEBUGREF\_INFO\_VALUE  
 構造体の初期化と `bstrValue` のフィールドを使用します。  
  
 DEBUGREF\_INFO\_ATTRIB  
 構造体の初期化と `dwAttrib` のフィールドを使用します。  
  
 DEBUGREF\_INFO\_REFTYPE  
 構造体の初期化と `dwRefType` のフィールドを使用します。  
  
 DEBUGREF\_INFO\_REF  
 構造体の初期化と `pReference` のフィールドを使用します。  
  
 DEBUGREF\_INFO\_VALUE\_AUTOEXPAND  
 このフィールド値はオブジェクトの型に自動配置された値を可能であれば含める必要があります。  
  
 DEBUGREF\_INFO\_NONE  
 フラグが設定されていないことを示します。  
  
 DEBUGREF\_INFO\_ALL  
 フラグのマスクを示します。  
  
## 解説  
 これらのフラグは [EnumChildren](../Topic/IDebugReference2::EnumChildren.md) と [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) のメソッドに [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) の構造体のフィールドが初期化するかを示すために渡されます。  
  
 構造体が戻るときにフィールドを使用して有効かを示すために `DEBUG_REFERENCE_INFO` の構造体のメンバー `dwFields` に使用されます。  
  
 これらの値はビットごとの `OR` と組み合わせることがあります。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [EnumChildren](../Topic/IDebugReference2::EnumChildren.md)   
 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)