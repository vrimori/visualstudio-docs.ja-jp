---
title: IDebugBinder3::FindAlias |Microsoft Docs
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
ms.openlocfilehash: 128629f5cd359539406f438aec41909672e1ed83
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49837725"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
このメソッドは、名前、別名を検索します。 これでは、すべてのエイリアスをプログラムで検索します。  
  
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
 [out]エイリアス (あれば) が見つかりましたがによって表される、 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)インターフェイス。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`(エイリアスが存在しない) 場合はエラー コード。  
  
## <a name="remarks"></a>Remarks  
 このメソッドを呼び出す; 前に null 先となるオブジェクトを初期化しますエイリアスが見つかったかどうかを決定した後に null 値をテストします。  
  
## <a name="see-also"></a>関連項目  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)