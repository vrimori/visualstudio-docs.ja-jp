---
title: IDebugAddress::GetAddress |Microsoft Docs
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
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 323c3e8ea13b7809090d239acfaf5772b9e5b2d1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49839480"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

オブジェクトとそのスコープまたはコンテナー内の場所を記述する構造体を返します。  
  
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
 [入力、出力]A [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)にこのメソッドによって入力される構造体。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)このメソッドは、適切な情報でサインインし、格納する構造体が渡されます。 この情報を解釈する方法は、返される情報とシンボル ハンドラー自体の種類によって異なります。 参照してください[DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)の詳細。  
  
## <a name="see-also"></a>関連項目  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)

