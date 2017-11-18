---
title: "DEBUG_ADDRESS |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DEBUG_ADDRESS
helpviewer_keywords: DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a112e8b8d2204259fbd3ea003aef957a8c713abf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="debugaddress"></a>DEBUG_ADDRESS
この構造体では、アドレスを表します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _tagDEBUG_ADDRESS {  
   ULONG32             ulAppDomainID;  
   GUID                guidModule;  
   _mdToken            tokClass;  
   DEBUG_ADDRESS_UNION addr;  
} DEBUG_ADDRESS;  
```  
  
```csharp  
public struct DEBUG_ADDRESS {  
   public uint                ulAppDomainID;  
   public Guid                guidModule;  
   public int                 tokClass;  
   public DEBUG_ADDRESS_UNION addr;  
}  
```  
  
## <a name="terms"></a>用語  
 ulAppDomainID  
 プロセス id です。  
  
 guidModule  
 このアドレスを含むモジュールの GUID です。  
  
 tokClass  
 クラスまたはこのアドレスの種類を識別するトークンです。  
  
> [!NOTE]
>  この値は、シンボル プロバイダーに固有では、そのため、以外のクラス型の識別子としての一般的な意味を持ちません。  
  
 addr  
 A [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)構造で、個々 のアドレスの種類を記述する構造体の共用体が含まれています。 値`addr`です。`dwKind` [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)列挙体、共用体を解釈する方法について説明します。  
  
## <a name="remarks"></a>コメント  
 この構造体に渡される、 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)格納するメソッド。  
  
 **警告 [C++ のみ]**  
  
 場合`addr.dwKind`は`ADDRESS_KIND_METADATA_LOCAL`場合`addr.addr.addrLocal.pLocal`を呼び出す必要があります、null の値ではない`Release`トークンのポインターで。  
  
```  
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL &&  addr.addr.addrLocal.pLocal != NULL)  
{  
    addr.addr.addrLocal.pLocal->Release();  
}  
```  
  
## <a name="requirements"></a>要件  
 ヘッダー: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)