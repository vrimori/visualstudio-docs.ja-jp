---
title: IDebugProperty2::GetSize |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty2::GetSize
helpviewer_keywords:
- IDebugProperty2::GetSize
ms.assetid: 0deb8ec5-d6fb-4622-bb14-0c46b9459cc6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1b49ed63c95b63078880b554b31968d210cd063e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugproperty2getsize"></a>IDebugProperty2::GetSize
プロパティの値のバイト単位のサイズを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetSize (   
   DWORD* pdwSize  
);  
```  
  
```csharp  
int GetSize (   
   out uint pdwSize  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pdwSize`  
 [out]プロパティの値のバイト単位のサイズを返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`; エラー コードを返しますそれ以外の場合。 返します`S_GETSIZE_NO_SIZE`プロパティには、サイズがありません。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)