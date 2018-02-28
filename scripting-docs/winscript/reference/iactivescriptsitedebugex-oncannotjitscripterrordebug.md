---
title: "IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptSiteDebugEx.OnCanNotJITScriptErrorDebug
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
ms.assetid: 83f81476-bf12-47f2-897d-1d37d21137d4
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e428f12b3d199603ac341a5e069fcc5ce5d36f93
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebugexoncannotjitscripterrordebug"></a>IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
プロセス マネージャーをデバッグするときに、スクリプト実行時のエラーについて、ホストは、スクリプト デバッガーを時間内だけを見つけられませんに通知します。  
  
 デバッガーに、ホストを実装する必要がありますを処理する[IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)です。 ユーザー操作に基づいて、ホストできるか、デバッガーをアタッチし、返すを返したり、OnScriptErrorDebug でデバッガーの起動`pfEnterDebugger`パラメーター。 また、プロセスをデバッグ マネージャーで解釈できる外部のデバッガーがない場合でも、実行時エラーに関する通知を取得するには、このインターフェイスを実装する必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT OnCanNotJITScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug  
   BOOL *pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pErrorDebug`  
 [in]実行時エラーが発生しました。  
  
 `pfCallOnScriptErrorWhenContinuingt`  
 [out]呼び出すのか[IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)デバッグなしで続行する場合は、ユーザー。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 また、通知を取得するには、このインターフェイスを実装する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptSiteDebugEx インターフェイス](../../winscript/reference/iactivescriptsitedebugex-interface.md)