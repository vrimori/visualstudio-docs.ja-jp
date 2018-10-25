---
title: IDebugExpressionEvaluator::SetRegistryRoot |Microsoft Docs
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
- IDebugExpressionEvaluator::SetRegistryRoot
helpviewer_keywords:
- IDebugExpressionEvaluator::SetRegistryRoot method
ms.assetid: 790886d8-1975-4d3c-9a75-cd86c1faf4ca
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5d91ab4e3a4b46e9eb44346a91b88055cc6a4175
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49890467"
---
# <a name="idebugexpressionevaluatorsetregistryroot"></a>IDebugExpressionEvaluator::SetRegistryRoot
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このメソッドは、レジストリのルートを設定します。 サイド バイ サイドでのデバッグに使用します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT SetRegistryRoot (   
   LPCOLESTR ustrRegistryRoot  
);  
```  
  
```csharp  
int SetRegistryRoot(  
   string ustrRegistryRoot  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ustrRegistryRoot`  
 [in]新しいレジストリ ルート。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 指定されたレジストリ ルートは通常、式エバリュエーターが最初にインスタンス化され、ポイントしたときに設定を特定のバージョンの Visual Studio のレジストリ キー (hkey_local_machine \software\microsoft\visualstudio\\*X.Y*ここで、 *X.Y*はバージョン番号です)。  
  
## <a name="see-also"></a>関連項目  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)

