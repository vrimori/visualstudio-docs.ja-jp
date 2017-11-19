---
title: "IActiveScriptSiteDebug32::GetApplication |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 533d770d-06a4-4693-873e-255c9c6f0df0
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: bb7fdf5a6d0b380a8024cfdfa70282bcf80ba16d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebug32getapplication"></a>IActiveScriptSiteDebug32::GetApplication
このスクリプトのサイトに関連付けられているデバッグ アプリケーションのオブジェクトを返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppda`  
 [out]スクリプトのサイトに関連付けられているデバッグ アプリケーションのオブジェクトへのポインター。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
|`E_NOTIMPL`|ホストによって直接サポートされないデバッグします。|  
  
## <a name="remarks"></a>コメント  
 `GetApplication`メソッドは、各スクリプトが所属するアプリケーション オブジェクトを定義するスマート ホスト方法を提供します。 含む、アプリケーションを取得しを使用するには、このメソッドを呼び出すべきではスクリプト エンジン`IProcessDebugManager::GetDefaultApplication`これが失敗した場合。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptSiteDebug32 インターフェイス](../../winscript/reference/iactivescriptsitedebug32-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)