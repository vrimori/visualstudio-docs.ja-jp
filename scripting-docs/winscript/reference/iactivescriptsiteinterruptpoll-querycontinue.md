---
title: IActiveScriptSiteInterruptPoll::QueryContinue |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteInterruptPoll.QueryContinue
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteInterruptPoll::QueryContinue
ms.assetid: 41ac3807-f8b4-4a0e-bcc6-556bc89f3904
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93323d500ae7e99957c365d60741fa612ba0fc34
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725162"
---
# <a name="iactivescriptsiteinterruptpollquerycontinue"></a>IActiveScriptSiteInterruptPoll::QueryContinue
により、ホストは、スクリプトが終了することを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT QueryContinue();  
```  
  
#### <a name="parameters"></a>パラメーター  
 このメソッドには、パラメーターはありません。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|呼び出しが成功したし、ホストが継続して実行するスクリプトを許可します。|  
|`S_FALSE`|成功した呼び出しと、ホスト要求スクリプトは終了です。|  
  
## <a name="remarks"></a>コメント  
 ホストされているスクリプトを終了する場合を除き、戻り値の`QueryContinue`メソッドは`S_OK`します。 戻り値の`S_FALSE`ホスト明示的に要求するスクリプトが終了することを示します。  
  
 マルチ スレッドのホストが使用する可能性があります、`IActiveScript::InterruptScriptThread`メソッドをスクリプトを終了します。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptSiteInterruptPoll インターフェイス](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)