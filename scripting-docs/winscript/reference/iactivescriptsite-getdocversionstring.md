---
title: IActiveScriptSite::GetDocVersionString |Microsoft Docs
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
ms.openlocfilehash: a451f4883373978772643e11fe22feb9122be30e
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349752"
---
# <a name="iactivescriptsitegetdocversionstring"></a>IActiveScriptSite::GetDocVersionString
現在のドキュメントのバージョンを一意に識別するホスト定義の文字列を取得します。 (メモ帳で編集されている HTML ページの大文字と小文字) のように Windows スクリプトのスコープ外関連のドキュメントを変更した場合は、スクリプト エンジン保存できますこのと共に強制的に再コンパイル、スクリプトが読み込まれる、次回の永続化された状態。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pstrVersionString`  
 [out]ホストが定義するドキュメントのバージョン文字列のアドレス。  
  
## <a name="return-value"></a>戻り値  
 返します`S_OK`成功した場合、または`E_NOTIMPL`場合、このメソッドはサポートされていません。  
  
## <a name="remarks"></a>Remarks  
 場合`E_NOTIMPL`返されるか、スクリプト エンジンでは、スクリプトは、ドキュメントとの同期にすると想定する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)