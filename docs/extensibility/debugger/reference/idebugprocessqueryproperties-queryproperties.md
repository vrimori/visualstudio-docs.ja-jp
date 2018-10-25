---
title: IDebugProcessQueryProperties::QueryProperties |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugProcessQueryProperties::QueryProperties
ms.assetid: 976a9962-b689-45bb-afb6-16b2c5dbc3b8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 37abff77fa0c969be7186413f0e3e2531c8d94d6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915400"
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