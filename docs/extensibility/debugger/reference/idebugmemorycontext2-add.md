---
title: "IDebugMemoryContext2::Add |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMemoryContext2::Add
helpviewer_keywords:
- IDebugMemoryContext2::Add method
- Add method
ms.assetid: 3c47e646-ce9e-4dd3-8f1a-6dbd3827d407
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 4f06d8e80bcaecefa515ae4ca0b0bd46cab1ca8d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="see-also"></a>参照  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)