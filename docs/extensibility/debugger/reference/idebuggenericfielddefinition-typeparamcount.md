---
title: "IDebugGenericFieldDefinition::TypeParamCount | Microsoft Docs"
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
  - "TypeParamCount"
  - "IDebugGenericFieldDefinition::TypeParamCount"
ms.assetid: d41dd5ea-aa25-4bf3-bcfd-e0bf451ead49
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugGenericFieldDefinition::TypeParamCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

[標準] フィールドに関連付けられている型パラメーターの数を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT TypeParamCount(  
   ULONG32* pcParams  
);  
```  
  
```c#  
int TypeParamCount(  
   ref uint pcParams  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pcParams`  
 [入力、出力]型パラメーターの数。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返す `S_OK`。 そうしないと、エラー コードを返します。  
  
## <a name="remarks"></a>解説  
 場合一覧 \< T>, 、このメソッドには、1 が返された場合はリスト \< T1, T2 > 2 を返します。 このメソッドは、型パラメーターがない場合に 0 を返します。  
  
## <a name="see-also"></a>参照  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)