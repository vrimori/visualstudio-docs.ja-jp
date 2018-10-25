---
title: IDebugExpressionEvaluator2::GetService |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3c79663e8c274020f7e997bd638c3ae5b16ca874
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844810"
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

その一意識別子を指定したサービス オブジェクトを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetService (  
   GUID        uid,  
   IUnknown ** ppService  
);  
```  
  
```csharp  
int GetService (  
   Guid       uid,  
   out object ppService  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `uid`  
 [in]取得するサービスの一意の識別子。  
  
 `ppService`  
 [out]サービスを表すオブジェクトを返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 これは、別の式エバリュエーターからサービスを取得するサード パーティ製の式エバリュエーターで使用できます。 たとえば、このメソッドは、既定の式エバリュエーターからビジュアライザー サービスのインターフェイスを取得する使用でした。 サード パーティ製の式エバリュエーターされない可能性があるこのインターフェイスを実装する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)

