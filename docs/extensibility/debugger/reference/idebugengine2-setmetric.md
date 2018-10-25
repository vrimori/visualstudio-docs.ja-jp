---
title: IDebugEngine2::SetMetric |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine2:::SetMetric
helpviewer_keywords:
- IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 02f7d533cfc64ad7a1e3bfd342a2be56a5c6cd7a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49935953"
---
# <a name="idebugengine2setmetric"></a>IDebugEngine2::SetMetric
このメソッドは、メトリックと呼ばれるレジストリ値を設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetMetric(  
   LPCOLESTR pszMetric,  
   VARIANT   varValue  
);  
```  
  
```csharp  
int SetMetric(  
   string pszMetric,  
   object varValue  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pszMetric`  
 [in]メトリックの名前。  
  
 `varValue`  
 [in]メトリックの値を指定します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 メトリックは、使用またはサポートされている機能を提供するデバッグ エンジンの動作を変更するレジストリ値です。 このメソッドの適切な形式への呼び出しを転送できる、[デバッグ用の SDK ヘルパー](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)関数、`SetMetric`します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [デバッグ用の SDK ヘルパー](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)