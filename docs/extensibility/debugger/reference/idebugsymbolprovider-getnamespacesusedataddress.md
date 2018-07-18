---
title: IDebugSymbolProvider::GetNamespacesUsedAtAddress |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugSymbolProvider::GetNamespacesUsedAtAddress
helpviewer_keywords:
- IDebugSymbolProvider::GetNamespacesUsedAtAddress method
ms.assetid: 392de54b-9af0-4567-953b-1b41acd1e05c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 55befbc206b6b9c781c8dab75a110dbbcb6ea18d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122952"
---
# <a name="idebugsymbolprovidergetnamespacesusedataddress"></a>IDebugSymbolProvider::GetNamespacesUsedAtAddress
このメソッドは、デバッグ アドレスに関連付けられている名前空間の列挙子を作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetNamespacesUsedAtAddress(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int GetNamespacesUsedAtAddress(  
   IDebugAddress        pAddress,  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pAddress`  
 [in]デバッグのアドレス。  
  
 `ppEnum`  
 [out]返します、 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)名前空間の列挙子。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 ある可能性があります指定されたデバッグ アドレスに関連付けられているいくつかの名前空間は、名前空間、または複数の入れ子になった`using`ステートメントです。  
  
## <a name="see-also"></a>関連項目  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)