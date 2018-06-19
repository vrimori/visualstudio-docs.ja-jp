---
title: IActiveScriptSite::GetLCID |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetLCID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetLCID
ms.assetid: 7b4a2dc1-bcf6-4bbf-884e-97b305a28eb7
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a6e128f5ac5de11b45af59c83750411c35e6efa7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724812"
---
# <a name="iactivescriptsitegetlcid"></a>IActiveScriptSite::GetLCID
ホストのユーザー インターフェイスに関連付けられているロケール識別子を取得します。 スクリプト エンジンでは、識別子を使用して、エラー文字列と、エンジンによって生成された他のユーザー インターフェイス要素が適切な言語で表示されることを確認してください。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `plcid`  
 [out]スクリプト エンジンが表示されるユーザー インターフェイス要素のロケール識別子を受け取る変数のアドレスです。  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|戻り値|説明|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_NOTIMPL`|このメソッドは実装されていません。 システム定義のロケールを使用します。|  
|`E_POINTER`|無効なポインターが指定されました。|  
  
## <a name="remarks"></a>コメント  
 このメソッドが戻る場合`E_NOTIMPL`、システム定義のロケール識別子を使用する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)