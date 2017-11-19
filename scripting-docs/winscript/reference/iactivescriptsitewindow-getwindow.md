---
title: "IActiveScriptSiteWindow::GetWindow |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSiteWindow.GetWindow
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSiteWindow_GetWindow
ms.assetid: 6284e38c-9dfb-4d69-903d-f243f78c0331
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b3257ac5632a2f3d713b6329a9a1eeebc4415851
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitewindowgetwindow"></a>IActiveScriptSiteWindow::GetWindow
スクリプト エンジンを表示する必要がありますがポップアップ ウィンドウの所有者として機能するウィンドウへのハンドルを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetWindow(  
    HWND *phwnd  // address of variable for window handle  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `phwnd`  
 [out]ウィンドウ ハンドルを受け取る変数のアドレスです。  
  
## <a name="return-value"></a>戻り値  
 返します`S_OK`成功した場合、または`E_FAIL`場合はエラーが発生しました。  
  
## <a name="remarks"></a>コメント  
 このメソッドがに似ていますが、`IOleWindow::GetWindow`メソッドです。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)