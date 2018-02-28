---
title: "JsSetRuntimeMemoryLimit 関数 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsSetRuntimeMemoryLimit
helpviewer_keywords:
- JsSetRuntimeMemoryLimit function
ms.assetid: 74feb31f-19f6-43e3-b117-0694c59ac593
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 587eb369e6971c7527177624ccf5baf839246cf9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="jssetruntimememorylimit-function"></a>JsSetRuntimeMemoryLimit 関数
ランタイムの現在のメモリ制限を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeMemoryLimit(  
   _In_ JsRuntimeHandle runtime,  
   _In_ size_t memoryLimit  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `runtime`  
 メモリ制限を設定するランタイム。  
  
 `memoryLimit`  
 新しいランタイム メモリ制限 (バイト)、またはメモリ制限がない場合は -1。  
  
## <a name="return-value"></a>戻り値  
 操作が成功した場合はコード `JsNoError` 、操作が失敗した場合はエラー コード。  
  
## <a name="remarks"></a>コメント  
 メモリ制限により、該当する制限を超えるすべての操作が「メモリ不足」エラーにより失敗します。 ランタイムのメモリ制限に -1 を設定すると、ランタイムにメモリ制限がないことを示します。 既定では新しいランタイムにメモリ制限はありません。 新しいメモリ制限が現在の使用量を上回る場合、呼び出しは成功します。以降このランタイムの割り当ては、ランタイムのメモリ使用量が制限以下に低下するまで失敗します。  
  
 ランタイムのメモリ制限は、別のスレッドでランタイムがアクティブであるかどうかにかかわらず、常に設定できます。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jsrt.h  
  
## <a name="see-also"></a>関連項目  
 [リファレンス (JavaScript ランタイム)](../chakra-hosting/reference-javascript-runtime.md)