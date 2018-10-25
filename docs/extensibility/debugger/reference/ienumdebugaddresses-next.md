---
title: IEnumDebugAddresses::Next |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugAddresses::Next
helpviewer_keywords:
- IEnumDebugAddresses::Next method
ms.assetid: 941e4be7-858d-433a-9259-18d0d017be9e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e8b027df9f723075f5cc20b5a7184595d0a1c8f9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49813389"
---
# <a name="ienumdebugaddressesnext"></a>IEnumDebugAddresses::Next
このメソッドは、列挙体から次の要素のセットを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Next(  
   ULONG           celt,  
   IDebugAddress** rgelt,  
   ULONG*          pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint            celt,  
   IDebugAddress[] rgelt,  
   ref uint        pceltFetched  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `celt`  
 [in]取得する要素の数。 最大サイズを指定します、`rgelt`配列。  
  
 `rgelt`  
 [入力、出力]配列[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)情報を格納する要素。  
  
 `pceltFetched`  
 [out]実際に返される要素の数を返します`rgelt`します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`します。 返します`S_FALSE`返される可能性があります、要求された要素数よりも少ない場合、それ以外の場合、エラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)