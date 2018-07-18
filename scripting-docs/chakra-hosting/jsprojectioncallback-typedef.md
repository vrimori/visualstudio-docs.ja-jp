---
title: JsProjectionCallback Typedef | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 32f22d37-e57e-4196-b6cd-a3fc75bd0632
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 80d1c64f04f44a8560c25935fba2a48905a73260
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568252"
---
# <a name="jsprojectioncallback-typedef"></a>JsProjectionCallback Typedef
正しいスレッドの `JsProjectionEnqueueCallback` に渡されたコンテキストによって呼び出される必要のある JsRT コールバック。  
  
## <a name="syntax"></a>構文  
  
```  
typedef void (CALLBACK *JsProjectionCallback)(  
  _In_ JsProjectionCallbackContext jsContext  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `jsContext`  
 コールバックを受信するには、 `JsSetProjectionEnqueueCallback` を呼び出す必要があります。  
  
## <a name="remarks"></a>コメント  
 この API は、エッジ モードでのみサポートされます。  
  
## <a name="requirements"></a>要件  
 jsrt.h  
  
## <a name="see-also"></a>関連項目  
 [リファレンス (JavaScript ランタイム)](../chakra-hosting/reference-javascript-runtime.md)