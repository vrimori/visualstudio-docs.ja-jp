---
title: "JsSetRuntimeMemoryAllocationCallback 関数 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsSetRuntimeMemoryAllocationCallback
helpviewer_keywords: JsSetRuntimeMemoryAllocationCallback function
ms.assetid: 6aa7d58d-6456-4df1-815f-1ba36fb4ae14
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 755ab36c8edb8c0350eb2b245e060344c8825dee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="jssetruntimememoryallocationcallback-function"></a>JsSetRuntimeMemoryAllocationCallback 関数
指定したランタイムのメモリ割り当てのコールバックを設定します  
  
## <a name="syntax"></a>構文  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeMemoryAllocationCallback(  
   _In_ JsRuntimeHandle runtime,  
   _In_opt_ void *callbackState,  
   _In_ JsMemoryAllocationCallback allocationCallback  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `runtime`  
 割り当てのコールバックを登録するランタイム。  
  
 `callbackState`  
 コールバックに返されるユーザー指定の状態。  
  
 `allocationCallback`  
 メモリ割り当てイベントに対して呼び出されるメモリ割り当てコールバック。  
  
## <a name="return-value"></a>戻り値  
 操作が成功した場合はコード `JsNoError` 、操作が失敗した場合はエラー コード。  
  
## <a name="remarks"></a>コメント  
 メモリ割り当てコールバックを登録すると、OS からのメモリの取得時または OS へのメモリの解放時に常に、ランタイムはホストに対するコールバックを行います。 このコールバック ルーチンは、ランタイム メモリ マネージャーがメモリ ブロックを割り当てる前に呼び出されます。 コールバックが false を返した場合、割り当ては拒否されます。 ランタイム メモリ マネージャーはまた、割り当ての失敗後と同様に、メモリ ブロックを解放した後、コールバック ルーチンを呼び出します。  
  
 コールバックは現在のランタイム実行スレッド上で呼び出されるため、コールバックが完了するまで実行がブロックされます。  
  
 コールバックの戻り値は格納されません。以前に拒否された割り当てによって、以後の新しいメモリ割り当てのためにランタイムが再度コールバックを呼び出すことは抑制されません。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jsrt.h  
  
## <a name="see-also"></a>関連項目  
 [リファレンス (JavaScript ランタイム)](../chakra-hosting/reference-javascript-runtime.md)