---
title: "IDebugMemoryBytes2::ReadAt |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f4c71da3152394442d63c937b77e4f6538fcc1ae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
指定された位置から始まるバイト シーケンスを読み取ります。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ReadAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory,  
   DWORD*                pdwRead,  
   DWORD*                pdwUnreadable  
);  
```  
  
```csharp  
int ReadAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory,  
   out uint             pdwRead,  
   ref uint             pdwUnreadable  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pStartContext`  
 [in][IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)バイトの読み取りを開始する場所を指定するオブジェクト。  
  
 `dwCount`  
 [in]読み取るバイト数。 指定の長さ、`rgbMemory`配列。  
  
 `rgbMemory`  
 [入力、出力].入力バイト配列が実際に読み取られます。  
  
 `pdwRead`  
 [out]実際に読み取られる連続するバイト数を返します。  
  
 `pdwUnreadable`  
 [入力、出力].読み取り不可能なバイト数を返します。 クライアントは、読み取り不可能なバイト数に興味がない場合、null 値を指定できます。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 かどうか 100 バイトが要求されたと読み取り可能な最初の 50、次の 20 は読み取り可能なあり、残りの 30 が読み取り可能なこのメソッドが返されます。  
  
 *`pdwRead` = 50  
  
 *`pdwUnreadable` = 20  
  
 この場合、ため`*pdwRead + *pdwUnreadable < dwCount`、呼び出し元が呼び出しを要求元の 100 の残りの 30 バイトの読み取りを行う必要があります、 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)に渡されたオブジェクト、`pStartContext`パラメーターの詳細を設定する必要がありますによって 70 です。  
  
## <a name="see-also"></a>参照  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)