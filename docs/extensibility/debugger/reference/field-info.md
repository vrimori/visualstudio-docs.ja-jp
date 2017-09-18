---
title: "FIELD_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FIELD_INFO"
helpviewer_keywords: 
  - "FIELD_INFO 構造体"
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# FIELD_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

この構造体にはローカル変数パラメーターまたはそのほかのフィールドついて説明します。  
  
## 構文  
  
```cpp#  
typedef struct _tagFieldInfo {   
   FIELD_INFO_FIELDS dwFields;  
   BSTR              bstrFullName;  
   BSTR              bstrName;  
   BSTR              bstrType;  
   FIELD_MODIFIERS   dwModifiers;  
} FIELD_INFO;  
```  
  
```c#  
public struct FIELD_INFO {  
   public uint   dwFields;  
   public string bstrFullName;  
   public string bstrName;  
   public string bstrType;  
   public uint   dwModifiers;  
};  
```  
  
## メンバー  
 dwFields  
 メンバーが設定されるかを指定する [FIELD\_INFO\_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) の列挙体のフラグの組み合わせ。  
  
 bstrFullName  
 フィールドの完全名。  
  
 bstrName  
 フィールドの短い形式の名前。  
  
 bstrType  
 フィールドの型。  
  
 dwModifiers  
 フィールドを説明する [FIELD\_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) の列挙体のフラグの組み合わせ。  
  
## 解説  
 この構造が表示される [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) のメソッドに渡されます。  
  
## 必要条件  
 ヘッダー : sh.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [FIELD\_INFO\_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)   
 [FIELD\_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)