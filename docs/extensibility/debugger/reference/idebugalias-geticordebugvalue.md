---
title: IDebugAlias::GetICorDebugValue |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bfe0d8e4734c0d836b2dc6009fdedfa264720778
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
このエイリアスに関連付けられている値を表すマネージ コード インターフェイスを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```csharp  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppUnk`  
 [out]`IUnknown`このエイリアスに関連付けられている値を表すインターフェイス。 このインターフェイスを照会することができます、`ICorDebugValue`インターフェイスです。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 このメソッドは、管理対象の値のみに適用されます (、`ICorDebugValue`でインターフェイスがある、[!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)]で指定されている、 [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] cordebug.idl ファイルに SDK)。  
  
## <a name="see-also"></a>関連項目  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)