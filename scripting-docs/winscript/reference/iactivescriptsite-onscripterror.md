---
title: "IActiveScriptSite::OnScriptError |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptSite.OnScriptError
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnScriptError
ms.assetid: 5c9c85cc-21ad-4232-be83-a24cc7570108
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4ae066fe7fa04a5c97dec618c65ccee3f90984a0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsiteonscripterror"></a>IActiveScriptSite::OnScriptError
エンジンが、スクリプトの実行中に実行エラーが発生したことをホストに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT OnScriptError(  
    IActiveScriptError *pase  // address of error interface  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pase`  
 [in]エラー オブジェクトのアドレス[IActiveScriptError](../../winscript/reference/iactivescripterror.md)インターフェイスです。 ホストは、実行エラーに関する情報を取得するのに、このインターフェイスを使用できます。  
  
## <a name="return-value"></a>戻り値  
 返します`S_OK`エラーは正しく処理される、またはそれ以外の場合、OLE にエラー コードが定義されている場合。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)