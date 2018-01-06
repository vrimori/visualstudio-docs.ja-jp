---
title: "IDebugBinder3::FindAlias |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBinder3::FindAlias
helpviewer_keywords: IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b88ae0da5f90da45d33ec56169665e9c8430846c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="see-also"></a>参照  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)