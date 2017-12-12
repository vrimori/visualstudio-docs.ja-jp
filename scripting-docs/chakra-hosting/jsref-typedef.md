---
title: JsRef Typedef | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6aafc39f-6b9c-457f-8bf0-48831bffe9b8
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d9d4c478a45f53e83dfa59fdde21cfa4c988c92e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="jsref-typedef"></a>JsRef Typedef
Chakra ガベージ コレクターが所有するオブジェクトへの参照。  
  
## <a name="syntax"></a>構文  
  
```  
typedef void *JsRef;  
```  
  
## <a name="remarks"></a>コメント  
 Chakra ランタイムは、JsRef 参照がローカル変数またはパラメーター (つまりスタック上) に格納されている限り、JsRef 参照を自動的に追跡します。 スタック以外の場所に JsRef を格納すると、オブジェクトの有効期間を管理するために、JsAddRef および JsRelease を呼び出す必要があります。そうしない場合、オブジェクトが使用中であってもガベージ コレクターによって解放されることがあります。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jsrt.h  
  
## <a name="see-also"></a>関連項目  
 [リファレンス (JavaScript ランタイム)](../chakra-hosting/reference-javascript-runtime.md)