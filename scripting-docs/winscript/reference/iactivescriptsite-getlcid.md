---
title: IActiveScriptSite::GetLCID |Microsoft Docs
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
ms.openlocfilehash: 959989d14d2a71f9c9eab4c78ef1b1bd9078362f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095005"
---
# <a name="iactivescriptsitegetlcid"></a>IActiveScriptSite::GetLCID
ホストのユーザー インターフェイスに関連付けられているロケール識別子を取得します。 スクリプト エンジンでは、識別子を使用して、エラー文字列と、エンジンによって生成されたその他のユーザー インターフェイス要素が適切な言語で表示されていることを確認します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `plcid`  
 [out]スクリプト エンジンによって表示されるユーザー インターフェイス要素のロケール識別子を受け取る変数のアドレス。  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|戻り値|説明|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_NOTIMPL`|このメソッドは実装されていません。 システム定義のロケールを使用します。|  
|`E_POINTER`|無効なポインターが指定されました。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドが戻る場合`E_NOTIMPL`、システム定義のロケール識別子を使用する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)