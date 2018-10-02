---
title: IDebugEngine2::SetMetric |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngine2:::SetMetric
helpviewer_keywords:
- IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2cae26f5dc6386ddaa0db9024ff53d5dd264a1d1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548697"
---
# <a name="idebugengine2setmetric"></a>IDebugEngine2::SetMetric
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugEngine2::SetMetric](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugengine2-setmetric)します。  
  
このメソッドは、メトリックと呼ばれるレジストリ値を設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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

