---
title: IActiveScriptSiteWindow::EnableModeless |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteWindow.EnableModeless
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteWindow_EnableModeless
ms.assetid: 83fe4f62-8e97-4f03-bc6f-d90aa888657d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7099fe7d13a1cb3231e67049104722af9373d7a8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724932"
---
# <a name="iactivescriptsitewindowenablemodeless"></a>IActiveScriptSiteWindow::EnableModeless
で有効にするにまたはメイン ウィンドウと同様、モードレス ダイアログ ボックスを無効にするホスト。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnableModeless(  
    BOOL fEnable  // enable flag  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `fEnable`  
 [in]場合は、フラグ`TRUE`、メイン ウィンドウに、モードレス ダイアログ ボックスを有効にまたは、 `FALSE`、無効にします。  
  
## <a name="return-value"></a>戻り値  
 返します`S_OK`成功した場合、または`E_FAIL`場合はエラーが発生しました。  
  
## <a name="remarks"></a>コメント  
 このメソッドは、`IOleInPlaceFrame::EnableModeless`メソッドです。  
  
 このメソッドの呼び出しを入れ子にすることができます。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)