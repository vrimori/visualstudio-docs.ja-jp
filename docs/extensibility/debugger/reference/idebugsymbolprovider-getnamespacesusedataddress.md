---
title: "IDebugSymbolProvider::GetNamespacesUsedAtAddress | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugSymbolProvider::GetNamespacesUsedAtAddress"
helpviewer_keywords: 
  - "IDebugSymbolProvider::GetNamespacesUsedAtAddress メソッド"
ms.assetid: 392de54b-9af0-4567-953b-1b41acd1e05c
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugSymbolProvider::GetNamespacesUsedAtAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このメソッドはデバッグのアドレスに関連付けられている名前空間の列挙子を作成します。  
  
## 構文  
  
```cpp#  
HRESULT GetNamespacesUsedAtAddress(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int GetNamespacesUsedAtAddress(  
   IDebugAddress        pAddress,  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### パラメーター  
 `pAddress`  
 \[入力\] デバッグのアドレス。  
  
 `ppEnum`  
 \[出力\] 名前空間の [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) の列挙子を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 特定のデバッグのアドレスたとえば入れ子になった名前空間または `using` 複数のステートメントが関連付けられた複数の名前空間あります。  
  
## 参照  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)