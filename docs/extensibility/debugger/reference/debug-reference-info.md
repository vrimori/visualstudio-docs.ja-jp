---
title: "DEBUG_REFERENCE_INFO | Microsoft Docs"
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
  - "DEBUG_REFERENCE_INFO"
helpviewer_keywords: 
  - "DEBUG_REFERENCE_INFO 構造体"
ms.assetid: 24b83d00-d756-42a1-8083-730f998761dc
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# DEBUG_REFERENCE_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

参照について説明します。  
  
## 構文  
  
```cpp#  
typedef struct tagDEBUG_REFERENCE_INFO {   
   DEBUGREF_INFO_FLAGS dwFields;  
   BSTR                bstrName;  
   BSTR                bstrType;  
   BSTR                bstrValue;  
   DBG_ATTRIB_FLAGS    dwAttrib;  
   REFERENCE_TYPE.     dwRefType;  
   IDebugReference2*   m_pReference;  
} DEBUG_REFERENCE_INFO;  
```  
  
```c#  
public struct DEBUG_REFERENCE_INFO {   
   public uint             dwFields;  
   public string           bstrName;  
   public string           bstrType;  
   public string           bstrValue;  
   public ulong            dwAttrib;  
   public uint.            dwRefType;  
   public IDebugReference2 m_pReference;  
};  
```  
  
## メンバー  
 dwFields  
 どのフィールドを表示するかを指定する [DEBUGREF\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) の列挙体のフラグの組み合わせ。  
  
 bstrName  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) のオブジェクトに対してユーザーが指定する名前。  
  
 bstrType  
 書式指定文字列として参照型。  
  
 bstrValue  
 書式設定された文字列値として参照  
  
 dwAttrib  
 デバッグのプロパティ属性のフラグを指定する [DBG\_ATTRIB\_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) の列挙体のフラグの組み合わせ。  
  
 dwRefType  
 参照型はまたは弱いかどうかを指定する [REFERENCE\_TYPE](../../../extensibility/debugger/reference/reference-type.md) の列挙体の値。  
  
 m\_pReference  
 リファレンス情報を指定する [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) のオブジェクト。  
  
## 解説  
 この構造が表示される [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) メソッドの呼び出しに渡されます。  この構造体も呼び出しから [EnumChildren](../Topic/IDebugReference2::EnumChildren.md) のメソッドに返される [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) インターフェイスの一覧の一部として返されます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DBG\_ATTRIB\_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [REFERENCE\_TYPE](../../../extensibility/debugger/reference/reference-type.md)   
 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)   
 [EnumChildren](../Topic/IDebugReference2::EnumChildren.md)   
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)