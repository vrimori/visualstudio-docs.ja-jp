---
title: IActiveScript::GetScriptSite |Microsoft Docs
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
ms.openlocfilehash: 85b7d94ccb9e2589b10bf705721fc289df9638a9
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094160"
---
# <a name="iactivescriptgetscriptsite"></a>IActiveScript::GetScriptSite
Windows スクリプト エンジンに関連付けられているサイト オブジェクトを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetScriptSite(  
    REFIID iid,           // interface identifier  
    void **ppvSiteObject  // address of host site interface  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `iid`  
 [in]要求されたインターフェイスの識別子。  
  
 `ppvSiteObject`  
 [out]ホストのサイト オブジェクトへのインターフェイス ポインターを受け取る場所のアドレス。  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|戻り値|説明|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引数が無効です。|  
|`E_NOINTERFACE`|指定したインターフェイスがサポートされていません。|  
|`E_POINTER`|無効なポインターが指定されました。|  
|`S_FALSE`|サイトは設定されません。`ppvSiteObject`にパラメーターが設定されている`NULL`します。|  
  
## <a name="see-also"></a>関連項目  
 [IActiveScript](../../winscript/reference/iactivescript.md)