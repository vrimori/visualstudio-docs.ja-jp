---
title: IActiveScriptSite::OnScriptError |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnScriptError
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnScriptError
ms.assetid: 5c9c85cc-21ad-4232-be83-a24cc7570108
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d2c9cb95615ad0b978cc7fd9943b687e5a7f3cac
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088414"
---
# <a name="iactivescriptsiteonscripterror"></a>IActiveScriptSite::OnScriptError
エンジンが、スクリプトの実行中に、実行エラーが発生したことをホストに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT OnScriptError(  
    IActiveScriptError *pase  // address of error interface  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pase`  
 [in]エラー オブジェクトのアドレス[IActiveScriptError](../../winscript/reference/iactivescripterror.md)インターフェイス。 ホストは、実行エラーに関する情報を取得するのにこのインターフェイスを使用できます。  
  
## <a name="return-value"></a>戻り値  
 返します`S_OK`エラーが正しく処理された、またはそれ以外の場合、OLE にエラー コードが定義されている場合。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)