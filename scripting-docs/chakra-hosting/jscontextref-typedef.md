---
title: JsContextRef Typedef | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8586bfcc-bb24-430d-a6f2-1a3b3e34ec2e
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec1300717b59c3b901665b39ca0102988e83e853
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="jscontextref-typedef"></a>JsContextRef Typedef
スクリプト コンテキストへの参照。  
  
## <a name="syntax"></a>構文  
  
```  
typedef JsRef JsContextRef;  
```  
  
## <a name="remarks"></a>コメント  
 各スクリプト コンテキストには、他のスクリプト コンテキスト内のグローバル オブジェクトとは異なる独自のグローバル オブジェクトが含まれます。  
  
 多くの Chakra ホスト API では、`JsSetCurrentContext` を使用して設定できる "アクティブ" なスクリプト コンテキストが必要です。 現在のコンテキストの設定を必要とする Chakra ホスト API は、ドキュメントで明示的に示されます。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jsrt.h  
  
## <a name="see-also"></a>関連項目  
 [リファレンス (JavaScript ランタイム)](../chakra-hosting/reference-javascript-runtime.md)