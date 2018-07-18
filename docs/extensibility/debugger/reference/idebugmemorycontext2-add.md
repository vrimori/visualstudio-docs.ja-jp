---
title: IDebugMemoryContext2::Add |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMemoryContext2::Add
helpviewer_keywords:
- IDebugMemoryContext2::Add method
- Add method
ms.assetid: 3c47e646-ce9e-4dd3-8f1a-6dbd3827d407
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ad55b81c1c4126efd69779e929521cfb94235ccc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31111935"
---
# <a name="idebugmemorycontext2add"></a>IDebugMemoryContext2::Add
現在のコンテキストに指定された値を追加し、新しいコンテキストを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Add(   
   UINT64                 dwCount,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```csharp  
int Add(  
   ulong                    dwCount,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwCount`  
 [in]現在のコンテキストに追加する値。  
  
 `ppMemCxt`  
 [out]新しいを返します[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 メモリ コンテキストは、新しいコンテキスト インターフェイスを必要とする新しいアドレスを生成するアドレス値を追加するために、アドレスです。  
  
 結果として得られるアドレスがこのコンテキストに関連付けられているメモリ空間の外にある場合でも、このメソッドは新しいコンテキストを生成常にする必要があります。 唯一の例外は、新しいコンテキストのメモリを割り当てることはできませんか`ppMemCxt`は、null 値 (エラー)。  
  
## <a name="see-also"></a>関連項目  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)