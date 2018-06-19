---
title: IDebugBinder3::FindAlias |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e68038f6e00c2a04f4c96f5f9d93fc4919d2fd09
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102123"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
このメソッドは、名前を指定、別名を検索します。 これは、プログラムのすべてのエイリアスを検索します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT FindAlias(  
   LPCOLESTR     pcstrName,  
   IDebugAlias** ppAlias  
);  
```  
  
```csharp  
int FindAlias(  
   string          pcstrName,  
   out IDebugAlias ppAlias  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pcstrName`  
 [in]検索するエイリアスの名前です。  
  
 `ppAlias`  
 [out]によって表されるエイリアスが見つかりました (存在する場合)、 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)インターフェイスです。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外を返します`S_FALSE`(エイリアスが見つからない) 場合はエラー コード。  
  
## <a name="remarks"></a>コメント  
 このメソッドを呼び出す; 前に null に変換先オブジェクトを初期化します。エイリアスが見つかりましたかどうかを決定した後に null 値をテストします。  
  
## <a name="see-also"></a>関連項目  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)