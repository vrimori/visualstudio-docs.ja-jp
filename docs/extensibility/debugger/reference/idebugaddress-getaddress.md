---
title: "IDebugAddress::GetAddress |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugAddress::GetAddress
helpviewer_keywords: IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3ed14b69dbc116514b191aadf58d209b4d39e458
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
オブジェクトとそのスコープまたはコンテナー内でその場所を記述する構造体を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetAddress (  
   DEBUG_ADDRESS * pAddress  
);  
```  
  
```csharp  
int GetAddress(  
   DEBUG_ADDRESS[] pAddress  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pAddress`  
 [入力、出力].A [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)にこのメソッドによって入力される構造です。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)このメソッドは、適切な情報を使用して格納する構造体が渡されます。 この情報を解釈する方法は、返される情報およびシンボル ハンドラー自体の種類によって異なります。 参照してください[DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)詳細についてはします。  
  
## <a name="see-also"></a>関連項目  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)