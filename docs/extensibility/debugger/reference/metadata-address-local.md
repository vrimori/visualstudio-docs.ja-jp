---
title: "METADATA_ADDRESS_LOCAL | Microsoft Docs"
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
  - "METADATA_ADDRESS_LOCAL"
helpviewer_keywords: 
  - "METADATA_ADDRESS_LOCAL 構造体"
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# METADATA_ADDRESS_LOCAL
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

この構造はスコープ内のローカル変数のアドレスを表します \(通常は関数またはメソッド\)。  
  
## 構文  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_LOCAL {  
   _mdToken  tokMethod;  
   IUnknown* pLocal;  
   DWORD     dwIndex;  
} METADATA_ADDRESS_LOCAL;  
```  
  
```c#  
public struct METADATA_ADDRESS_LOCAL {  
   public int    tokMethod;  
   public object pLocal;  
   public uint   dwIndex;  
}  
```  
  
## 用語  
 tokMethod  
 メソッドの ID はローカル変数とパーツ機能します。  
  
 \[C\+\+\] `_mdToken` は32 ビット `int` の `typedef` です。  
  
 pLocal  
 アドレスをこの構造体を表すトークン。  
  
 dwIndex  
 このメソッドまたは関数のローカル変数のインデックスまたは他の値です \(言語固有\)。  
  
## 解説  
 この構造は `DEBUG_ADDRESS_UNION` の構造体の `dwKind` のフィールドが `ADDRESS_KIND_LOCAL` \([ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) の列挙値\) に設定されている場合 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) の構造の共用体の一部です。  
  
 `pLocal` が null 以外の場合 `Warning:`\[C\+\+\]  のみこのトークン ポインターの `Release` を呼び出す必要があります \(`addr` は [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) の構造体のフィールドです\):  
  
```  
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL &&  addr.addr.addrLocal.pLocal != NULL)  
{  
    addr.addr.addrLocal.pLocal->Release();  
}  
```  
  
## 必要条件  
 ヘッダー : sh.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)