---
title: IDebugSymbolProvider::GetAddressesFromPosition |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition method
ms.assetid: 1b0f02cb-8ace-4614-88f3-0e10239012b3
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f729c6805a1d9b65cad2c2248a4873be9dd2a949
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49240137"
---
# <a name="idebugsymbolprovidergetaddressesfromposition"></a>IDebugSymbolProvider::GetAddressesFromPosition
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このメソッドは、デバッグ アドレスの配列にドキュメントの位置をマップします。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetAddressesFromPosition(   
   IDebugDocumentPosition2* pDocPos,  
   BOOL                     fStatmentOnly,  
   IEnumDebugAddresses**    ppEnumBegAddresses,  
   IEnumDebugAddresses**    ppEnumEndAddresses  
);  
```  
  
```csharp  
int GetAddressesFromPosition(   
   IDebugDocumentPosition2  pDocPos,  
   bool                     fStatmentOnly,  
   out IEnumDebugAddresses  ppEnumBegAddresses,  
   out IEnumDebugAddresses  ppEnumEndAddresses  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pDocPos`  
 [in]ドキュメントの位置。  
  
 `fStatmentOnly`  
 [in]TRUE の場合は、1 つのステートメントにデバッグ アドレスを制限します。  
  
 `ppEnumBegAddresses`  
 [out]このステートメントまたは行に関連付けられた開始デバッグ アドレスの列挙子を返します。  
  
 `ppEnumEndAddresses`  
 [out]返します、 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)このステートメントまたは行に関連付けられている終了のデバッグ アドレスの列挙子。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 ドキュメントの位置は、通常、ソース行の範囲を示します。 このメソッドを提供開始と、これらの行に関連付けられている終了デバッグ アドレス。 一部の言語では、複数の行または複数のステートメントを含む行にまたがるステートメントを使用できます。 このメソッドは、1 つのステートメントにデバッグ アドレスを制限するためのフラグを提供します。  
  
 テンプレートの場合と同様、複数のデバッグ アドレスを 1 つのステートメントのことができます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)

