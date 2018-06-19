---
title: IDebugPortSupplier3::EnumPersistedPorts |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
helpviewer_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
ms.assetid: 1c3dead3-5d6c-4067-8418-4015f0b0dd07
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4240a3ba82f3787c1e2e2da9f14c1cee5a8d177e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121106"
---
# <a name="idebugportsupplier3enumpersistedports"></a>IDebugPortSupplier3::EnumPersistedPorts
このメソッドは、永続化されたポートの一覧の列挙体をできるようにするオブジェクトを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumPersistedPorts(  
   BSTR_ARRAY         PortNames,  
   IEnumDebugPorts2** ppEnum  
);  
```  
  
```csharp  
int EnumPersistedPorts(  
   BSTR_ARRAY           PortNames,  
   out IEnumDebugPorts2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `PortNames`  
 [in]A [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)を検索し、永続化されたポートの間で返すポート名の一覧を含む構造体。 これらの名前で保存されるポートだけが返されます。  
  
 `ppEnum`  
 [out]実装するオブジェクト、 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)インターフェイスです。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 永続化されたポートは、ポート サプライヤーがインスタンス化、およびポート供給業者が破棄されるときに保存時に読み込まれます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)   
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)   
 [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)