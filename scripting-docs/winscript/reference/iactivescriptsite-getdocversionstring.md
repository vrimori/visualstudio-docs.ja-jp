---
title: IActiveScriptSite::GetDocVersionString |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetDocVersionString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetDocVersionString
ms.assetid: ab3f892d-06d3-4cb5-9ea5-20c4a1e518cd
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4b009c9eb40b2935a5b1aeca0d551819462bafc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724542"
---
# <a name="iactivescriptsitegetdocversionstring"></a>IActiveScriptSite::GetDocVersionString
現在のドキュメントのバージョンを一意に識別するホスト定義の文字列を取得します。 (メモ帳で編集されている HTML ページの場合) のようにスクリプトを Windows のスコープ外に関連するドキュメントを変更した場合、スクリプト エンジンで保存できますこのと共に強制的に再コンパイル次に、スクリプトが読み込まれるとき、永続化された状態。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pstrVersionString`  
 [out]ホストが定義するドキュメントのバージョン文字列のアドレス。  
  
## <a name="return-value"></a>戻り値  
 返します`S_OK`成功した場合、または`E_NOTIMPL`場合、このメソッドはサポートされていません。  
  
## <a name="remarks"></a>コメント  
 場合`E_NOTIMPL`返されるか、スクリプト エンジンがスクリプトがドキュメントとの同期を想定する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)