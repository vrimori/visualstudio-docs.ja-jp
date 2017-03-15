---
title: "FIELD_INFO_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FIELD_INFO_FIELDS"
helpviewer_keywords: 
  - "FIELD_INFO_FIELDS 列挙型"
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# FIELD_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

[IDebugField](../../../extensibility/debugger/reference/idebugfield.md) のオブジェクトに関して取得する情報を指定します。  
  
## 構文  
  
```cpp#  
enum enum_FIELD_INFO_FIELDS {   
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
typedef DWORD FIELD_INFO_FIELDS;  
```  
  
```c#  
public enum enum_FIELD_INFO_FIELDS {  
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
```  
  
## メンバー  
 FIF\_FULLNAME  
 [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md) の構造体の初期化と `bstrFullName` のフィールドを使用します。  
  
 FIF\_NAME  
 `FIELD_INFO` の構造体の初期化と `bstrName` のフィールドを使用します。  
  
 FIF\_TYPE  
 `FIELD_INFO` の構造体の初期化と `bstrType` のフィールドを使用します。  
  
 FIF\_MODIFIERS  
 `FIELD_INFO` の構造体の初期化と `bstrModifiers` のフィールドを使用します。  
  
## 解説  
 [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md) の構造体のフィールドが初期化する方法を指定するには次の値も [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) ため引数のメソッドに渡されます。  
  
 `FIELD_INFO` の構造体の `dwFields` のメンバーはこれらの値がどのフィールドが使用され有効かを示すために使用されます。  
  
 これらのフラグはビットごと `OR` に組み合わせることがあります。  
  
## 必要条件  
 ヘッダー : sh.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)