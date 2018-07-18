---
title: IActiveScriptParse32::InitNew |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c77aa16-f391-4c93-9f1a-4e529a9930b2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 31de8258ae13855741c6dd5ca9e4ff2c589e97bf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645792"
---
# <a name="iactivescriptparse32initnew"></a>IActiveScriptParse32::InitNew
スクリプト エンジンを初期化します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>戻り値  
 返します`S_OK`成功した場合、または`E_FAIL`の初期化中にエラーが発生した場合。  
  
## <a name="remarks"></a>コメント  
 スクリプト エンジンを使用することができます、前に、次のメソッドのいずれかを呼び出さなければなりません: `IPersist*::Load`、 `IPersist*::InitNew`、または`IActiveScriptParse32::InitNew`です。 このメソッドのセマンティクスは次と同じ`IPersistStreamInit::InitNew`点で、この方法では、スクリプト エンジンでそれ自体を初期化するために、します。 両方の呼び出しは無効ではないことに注意`IPersist*::InitNew`または`IActiveScriptParse32::InitNew`と`IPersist*::Load`でもなく、呼び出しは無効`IPersist*::InitNew`、 `IActiveScriptParse32::InitNew`、または`IPersist*::Load`も複数回です。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)