---
title: IDebugSymbolProvider::GetAddressesFromContext |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromContext
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromContext method
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b7fbea573bf7a62770109b9933a977a3f0dca0e7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54938682"
---
# <a name="idebugsymbolprovidergetaddressesfromcontext"></a>IDebugSymbolProvider::GetAddressesFromContext
このメソッドは、ドキュメントのコンテキストをデバッグ アドレスの配列にマップします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetAddressesFromContext(   
   IDebugDocumentContext2* pDocContext,  
   BOOL                    fStatmentOnly,  
   IEnumDebugAddresses**   ppEnumBegAddresses,  
   IEnumDebugAddresses**   ppEnumEndAddresses  
);  
```  
  
```csharp  
int GetAddressesFromContext(  
   IDebugDocumentContext2  pDocContext,  
   bool                    fStatmentOnly,  
   out IEnumDebugAddresses ppEnumBegAddresses,  
   out IEnumDebugAddresses ppEnumEndAddresses  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pDocContext`  
 [in]ドキュメントのコンテキスト。  
  
 `fStatmentOnly`  
 [in]TRUE の場合は、1 つのステートメントにデバッグ アドレスを制限します。  
  
 `ppEnumBegAddresses`  
 [out]このステートメントまたは行に関連付けられた開始デバッグ アドレスの列挙子を返します。  
  
 `ppEnumEndAddresses`  
 [out]返します、 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)このステートメントまたは行に関連付けられている終了のデバッグ アドレスの列挙子。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 ドキュメントのコンテキストは、通常、ソース行の範囲を示します。 このメソッドを提供開始と、これらの行に関連付けられている終了デバッグ アドレス。 一部の言語では、複数の行または複数のステートメントを含む行にまたがるステートメントを使用できます。 このメソッドは、1 つのステートメントにデバッグ アドレスを制限するためのフラグを提供します。  
  
 テンプレートの場合と同様、複数のデバッグ アドレスを 1 つのステートメントのことができます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)   
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)