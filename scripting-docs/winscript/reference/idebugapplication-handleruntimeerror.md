---
title: "IDebugApplication::HandleRuntimeError |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugApplication.HandleRuntimeError
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::HandleRuntimeError
ms.assetid: f8f3bbaf-09e5-4d01-8a35-f380bc7ff8ed
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eead4780ff061ff9c7280aeee0936c8f64741981
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationhandleruntimeerror"></a>IDebugApplication::HandleRuntimeError
現在のスレッドをブロックして、デバッガーの IDE にエラーの通知を送信します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT HandleRuntimeError(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   IActiveScriptSite*        pScriptSite,  
   BREAKRESUMEACTION*        pbra,  
   ERRORRESUMEACTION*        perra,  
   BOOL*                     pfCallOnScriptError  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pErrorDebug`  
 [in]発生したエラー。  
  
 `pScriptSite`  
 [in]スレッドのスクリプト サイトです。  
  
 `pbra`  
 [out]デバッガーは、アプリケーションを再開したときに実行するアクション。  
  
 `perra`  
 [out]デバッガーは、エラーがある場合に、アプリケーションを再開したときに実行するアクション。  
  
 `pfCallOnScriptError`  
 [out]これはフラグ`TRUE`場合は、エンジンを呼び出す必要があります、`IActiveScriptSite::OnScriptError`メソッドです。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 言語エンジンは、実行時エラーが発生するスレッドのコンテキストでこのメソッドを呼び出します。 このメソッドは、現在のスレッドをブロックするし、IDE のデバッガーに送信されるエラーの通知を送信します。 デバッガーの IDE では、アプリケーションが再開される、このメソッドは、実行するアクションを返します。  
  
> [!NOTE]
>  実行時エラーの中にスタック フレームを列挙または式の評価は、このようなタスクを実行するスレッドによって言語エンジンを呼び出すことができます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugApplication インターフェイス](../../winscript/reference/idebugapplication-interface.md)   
 [IActiveScriptErrorDebug インターフェイス](../../winscript/reference/iactivescripterrordebug-interface.md)   
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)   
 [BREAKRESUMEACTION 列挙型](../../winscript/reference/breakresumeaction-enumeration.md)   
 [ERRORRESUMEACTION 列挙型](../../winscript/reference/errorresumeaction-enumeration.md)