---
title: IActiveScriptParse::InitNew |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParse.InitNew
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_InitNew
ms.assetid: 3a582bd6-fc0d-43a5-812f-5ea55a8517a1
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e34094bcc25c0316fa670f570d8b2664acc0ba78
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724482"
---
# <a name="iactivescriptparseinitnew"></a>IActiveScriptParse::InitNew
スクリプト エンジンを初期化します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>戻り値  
 返します`S_OK`成功した場合、または`E_FAIL`の初期化中にエラーが発生した場合。  
  
## <a name="remarks"></a>コメント  
 スクリプト エンジンを使用することができます、前に、次のメソッドのいずれかを呼び出さなければなりません: `IPersist*::Load`、 `IPersist*::InitNew`、または`IActiveScriptParse::InitNew`です。 このメソッドのセマンティクスは次と同じ`IPersistStreamInit::InitNew`点で、この方法では、スクリプト エンジンでそれ自体を初期化するために、します。 両方の呼び出しは無効ではないことに注意`IPersist*::InitNew`または`IActiveScriptParse::InitNew`と`IPersist*::Load`でもなく、呼び出しは無効`IPersist*::InitNew`、 `IActiveScriptParse::InitNew`、または`IPersist*::Load`も複数回です。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)