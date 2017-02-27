---
title: "DEBUG_ADDRESS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEBUG_ADDRESS"
helpviewer_keywords: 
  - "DEBUG_ADDRESS 構造体"
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# DEBUG_ADDRESS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

この構造体はアドレスを表します。  
  
## 構文  
  
```cpp  
typedef struct _tagDEBUG_ADDRESS {  
   ULONG32             ulAppDomainID;  
   GUID                guidModule;  
   _mdToken            tokClass;  
   DEBUG_ADDRESS_UNION addr;  
} DEBUG_ADDRESS;  
```  
  
```c#  
public struct DEBUG_ADDRESS {  
   public uint                ulAppDomainID;  
   public Guid                guidModule;  
   public int                 tokClass;  
   public DEBUG_ADDRESS_UNION addr;  
}  
```  
  
## 用語  
 ulAppDomainID  
 プロセス ID  
  
 guidModule  
 このアドレスを含むモジュールの GUID。  
  
 tokClass  
 このアドレスのクラスまたは型を識別するトークン。  
  
> [!NOTE]
>  この値はシンボルのプロバイダーに固有でクラス型の識別子としてではなく一般的な意味がありません。  
  
 アドレス  
 個々のアドレスの種類を示す構造体の共用体を含む [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) の構造体。  値 `addr`。`dwKind` は共用体を解釈する方法を説明する [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) の列挙体から取得されます。  
  
## 解説  
 この構造が表示される [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) のメソッドに渡されます。  
  
 **警告のみ \[C\+\+\]**  
  
 `addr.dwKind` が `ADDRESS_KIND_METADATA_LOCAL` で`addr.addr.addrLocal.pLocal` が null 値でない場合トークンのポインター `Release` を呼び出す必要があります :  
  
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
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)