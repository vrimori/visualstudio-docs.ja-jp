---
title: IDebugMemoryContext2::Subtract |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugMemoryContext2::Subtract
helpviewer_keywords:
- Subtract method
- IDebugMemoryContext2::Subtract method
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 78304d49ac3b921b4930f94f7f3ac2573e46b82d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49831304"
---
# <a name="idebugmemorycontext2subtract"></a>IDebugMemoryContext2::Subtract
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

現在のコンテキストから指定された値を減算し、新しいコンテキストを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT Subtract(   
   UINT64                 dwCount,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```csharp  
int Subtract(  
   ulong                    dwCount,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwCount`  
 [in]デクリメントするメモリのバイト数。  
  
 `ppMemCxt`  
 [out]新しいを返します[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 メモリのコンテキストは、アドレスからの値を減算したコンテキストの新しいインターフェイスを必要とする新しいアドレスを生成するために、アドレスです。  
  
 結果として得られるアドレスがこのコンテキストに関連付けられたメモリ空間の外にある場合でも、新しいコンテキストをこのメソッドを生成することが常にする必要があります。 唯一の例外は、新しいコンテキストのメモリを割り当てることはできませんか場合`ppMemCxt`は (つまり、エラー)、null 値です。  
  
## <a name="see-also"></a>関連項目  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)

