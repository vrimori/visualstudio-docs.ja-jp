---
title: "IEnumDebugPropertyInfo2::Next |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumDebugPropertyInfo2::Next
helpviewer_keywords:
- IEnumDebugPropertyInfo2::Next
ms.assetid: 4eb8c7c3-aadf-4187-abee-c0620308a3eb
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 5f97a63ae9da055d40b1c6cbe3d91bf343aee067
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="ienumdebugpropertyinfo2next"></a>IEnumDebugPropertyInfo2::Next
列挙体から次の要素のセットを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Next(  
   ULONG                 celt,  
   DEBUG_PROPERTY_INFO** rgelt,  
   ULONG*                pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint                  celt,  
   DEBUG_PROPERTY_INFO[] rgelt,  
   ref uint              pceltFetched  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `celt`  
 [in]取得する要素の数。 また、最大のサイズを指定、`rgelt`配列。  
  
 `rgelt`  
 [入力、出力].配列[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)格納する要素。  
  
 `pceltFetched`  
 [out]実際に返される要素の数を返します`rgelt`です。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`です。 返します`S_FALSE`要求された要素数より少ないは返されませんでした。 それ以外の場合、エラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
