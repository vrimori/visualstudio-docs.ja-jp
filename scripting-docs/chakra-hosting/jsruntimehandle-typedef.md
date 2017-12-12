---
title: JsRuntimeHandle Typedef | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 69e59bfd-9b0e-4710-9aa8-fbd6844171bc
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d3c0344e203c58691048c55ba4080c6c86c1c643
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="jsruntimehandle-typedef"></a>JsRuntimeHandle Typedef
Chakra ランタイムへのハンドル。  
  
## <a name="syntax"></a>構文  
  
```  
typedef void *JsRuntimeHandle;  
```  
  
## <a name="remarks"></a>コメント  
 各 Chakra ランタイムには、独自の独立した実行エンジン、JIT コンパイラ、およびガベージ コレクション ヒープがあります。 このために、各ランタイムは他のランタイムから完全に分離されています。  
  
 ランタイムは、任意のスレッドで使用できますが、任意の時点で 1 つのスレッドのみがランタイムを呼び出すことができます。  
  
> [!WARNING]
>  JsRuntimeHandle は、Chakra ホスト API の他のオブジェクト参照とは異なり、ガベージ コレクション ヒープ自体を含むので、ガベージ コレクションは行われません。 ランタイムは、JsDisposeRuntime を呼び出すまで存続します。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jsrt.h  
  
## <a name="see-also"></a>関連項目  
 [リファレンス (JavaScript ランタイム)](../chakra-hosting/reference-javascript-runtime.md)