---
title: IActiveScriptSiteWindow::GetWindow |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteWindow.GetWindow
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteWindow_GetWindow
ms.assetid: 6284e38c-9dfb-4d69-903d-f243f78c0331
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 268a54ccdcbd70ed159758720db0735f16d81492
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349050"
---
# <a name="iactivescriptsitewindowgetwindow"></a>IActiveScriptSiteWindow::GetWindow
スクリプト エンジンを表示する必要がある、ポップアップ ウィンドウの所有者として機能できるウィンドウのハンドルを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetWindow(  
    HWND *phwnd  // address of variable for window handle  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `phwnd`  
 [out]ウィンドウ ハンドルを受け取る変数のアドレス。  
  
## <a name="return-value"></a>戻り値  
 返します`S_OK`成功した場合、または`E_FAIL`場合は、エラーが発生しました。  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、`IOleWindow::GetWindow`メソッド。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)