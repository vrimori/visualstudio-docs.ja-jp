---
title: "BUILT_TYPE | Microsoft Docs"
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
  - "BUILT_TYPE"
helpviewer_keywords: 
  - "BUILT_TYPE 構造体"
ms.assetid: cc02c32c-0f65-4210-ad25-a9b1899066e8
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# BUILT_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

この構造体はメタデータから取得したフィールドの種類についての情報を指定します。  
  
## 構文  
  
```cpp#  
typedef struct _tagTYPE_BUILT {  
   ULONG32      ulAppDomainID;  
   GUID         guidModule;  
   IDebugField* pUnderlyingField;  
} BUILT_TYPE;  
```  
  
```c#  
public struct BUILT_TYPE {  
   public uint        ulAppDomainID;  
   public Guid        guidModule;  
   public IDebugField pUnderlyingField;  
};  
```  
  
#### パラメーター  
 ulAppDomainID  
 シンボルがアプリケーションの ID。  これはアプリケーションのインスタンスを識別するために使用されます。  
  
 guidModule  
 このフィールドを含むモジュールの GUID。  
  
 pUnderlyingField  
 この組み込みフィールドに関連付けられている基になるフィールドを指定する [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) のオブジェクト。  
  
## 解説  
 この構造は [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md) の構造の共用体の一部として `TYPE_INFO` の構造体の `dwKind` のフィールドが `TYPE_KIND_BUILT` \([dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) の列挙値\) に設定すると表示されます。  
  
## 必要条件  
 ヘッダー : sh.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)