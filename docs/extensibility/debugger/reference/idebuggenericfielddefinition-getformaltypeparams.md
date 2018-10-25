---
title: IDebugGenericFieldDefinition::GetFormalTypeParams |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetFormalTypeParams
- IDebugGenericFieldDefinition::GetFormalTypeParams
ms.assetid: cadbd6a1-bc7c-4aff-8777-5396b7a23c3e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0827947050df1258d8b062d00b579fc1608d2c77
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49823593"
---
# <a name="idebuggenericfielddefinitiongetformaltypeparams"></a>IDebugGenericFieldDefinition::GetFormalTypeParams
パラメーターの数を指定された型パラメーターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetFormalTypeParams(  
   ULONG32                   cParams,  
   IDebugGenericParamField** ppParams,  
   ULONG32*                  pcParams  
);  
```  
  
```csharp  
int GetFormalTypeParams(  
   uint                          cParams,  
   out IDebugGenericParamField[] ppParams,  
   ref uint                      pcParams  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `cParams`  
 [in]パラメーターの数。  
  
 `ppParams`  
 [out]型パラメーターの配列。  
  
 `pcParams`  
 [入力、出力]パラメーターの数、`ppParams`配列。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 右の順序で左からの型パラメーターを返します。 例: Dictionary\<K, V > IDebugFormalGenericParameters {K, V} を返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)