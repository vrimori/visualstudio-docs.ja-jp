---
title: IActiveScript::GetScriptSite |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptSite
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptSite
ms.assetid: 83a2a89d-93d0-4cbd-9244-91a730cb406b
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 961483d45c72018bc216306d6c1aba0400a367ad
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640372"
---
# <a name="iactivescriptgetscriptsite"></a>IActiveScript::GetScriptSite
Windows スクリプト エンジンに関連付けられているサイト オブジェクトを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetScriptSite(  
    REFIID iid,           // interface identifier  
    void **ppvSiteObject  // address of host site interface  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `iid`  
 [in]要求されたインターフェイスの識別子。  
  
 `ppvSiteObject`  
 [out]ホストのサイト オブジェクトへのインターフェイス ポインターを受け取る場所のアドレスです。  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|戻り値|説明|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引数が無効です。|  
|`E_NOINTERFACE`|指定されたインターフェイスがサポートされていません。|  
|`E_POINTER`|無効なポインターが指定されました。|  
|`S_FALSE`|サイトが設定されていません。`ppvSiteObject`にパラメーターが設定されている`NULL`です。|  
  
## <a name="see-also"></a>関連項目  
 [IActiveScript](../../winscript/reference/iactivescript.md)