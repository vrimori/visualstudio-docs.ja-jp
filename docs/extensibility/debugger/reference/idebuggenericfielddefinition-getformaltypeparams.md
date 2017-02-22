---
title: "IDebugGenericFieldDefinition::GetFormalTypeParams | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetFormalTypeParams"
  - "IDebugGenericFieldDefinition::GetFormalTypeParams"
ms.assetid: cadbd6a1-bc7c-4aff-8777-5396b7a23c3e
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugGenericFieldDefinition::GetFormalTypeParams
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

パラメーターの数を指定した型のパラメーターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetFormalTypeParams(  
   ULONG32                   cParams,  
   IDebugGenericParamField** ppParams,  
   ULONG32*                  pcParams  
);  
```  
  
```c#  
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
 [入力、出力]パラメーターの数、 `ppParams` 配列。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返す `S_OK`。 そうしないと、エラー コードを返します。  
  
## <a name="remarks"></a>解説  
 右の順序で左からの型パラメーターを返します。 たとえば、Dictionary \< K, V > は、IDebugFormalGenericParameters {K, V} を返します。  
  
## <a name="see-also"></a>参照  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)