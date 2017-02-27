---
title: "IDebugAlias::GetICorDebugValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugAlias::GetICorDebugValue"
helpviewer_keywords: 
  - "IDebugAlias::GetICorDebugValue メソッド"
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugAlias::GetICorDebugValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このエイリアスに関連付けられている値を表すマネージ コード インターフェイスを取得します。  
  
## 構文  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```c#  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### パラメーター  
 `ppUnk`  
 \[out\] `IUnknown` このエイリアスに関連付けられている値を表すインターフェイスです。 このインターフェイスを照会できる、 `ICorDebugValue` インターフェイスです。  
  
## 戻り値  
 成功した場合、S\_OK を返します。それ以外の場合、エラー コードを返します。  
  
## 解説  
 このメソッドは、管理対象の値のみに適用されます \(、 `ICorDebugValue` でインターフェイスがある、 [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] で指定されている、 [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] SDK cordebug.idl ファイルに\)。  
  
## 参照  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)