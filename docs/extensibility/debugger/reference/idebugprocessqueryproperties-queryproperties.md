---
title: IDebugProcessQueryProperties::QueryProperties |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugProcessQueryProperties::QueryProperties
ms.assetid: 976a9962-b689-45bb-afb6-16b2c5dbc3b8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 548140afa666bd3178928fa650773bf765812a25
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53924528"
---
# <a name="idebugprocessquerypropertiesqueryproperties"></a>IDebugProcessQueryProperties::QueryProperties
このメソッドは、デバッグ プロセスの指定したプロパティ値のクエリを実行します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT QueryProperties(  
   ULONG                  celt,  
   PROCESS_PROPERTY_TYPE *rgdwPropTypes,  
   VARIANT               *rgtPropValues);  
```  
  
```csharp  
int QueryProperties(  
   uint                       celt,  
   enum_PROCESS_PROPERTY_TYPE rgdwPropTypes,  
   out object[ ]              rgtPropValues);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `celt`  
 [in]プロパティの定義とプロパティの値を含む配列のサイズ。  
  
 `dwPropType`  
 [in]クエリ対象のプロパティの定義を含む配列。 次の値を指定できます。  
  
- PROCESS_PROPERTY_COMMAND_LINE = 1  
  
- PROCESS_PROPERTY_CURRENT_DIRECTORY = 2  
  
- PROCESS_PROPERTY_ENVIRONMENT_VARIABLES 3 を =  
  
  `pvarPropValue`  
  [out]プロパティ値を格納する配列。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドが使用されることはほとんどありません。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProcessQueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties.md)