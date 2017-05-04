---
title: "IActiveScriptSiteWindow::GetWindow | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteWindow.GetWindow
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteWindow_GetWindow"
ms.assetid: 6284e38c-9dfb-4d69-903d-f243f78c0331
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteWindow::GetWindow
表示するスクリプト エンジンがあるポップアップ ウィンドウのオーナーとして機能するウィンドウへのハンドルを取得します。  
  
## 構文  
  
```  
HRESULT GetWindow(  
    HWND *phwnd  // address of variable for window handle  
);  
```  
  
#### パラメーター  
 `phwnd`  
 \[出力\]ウィンドウ ハンドルを受け取る変数のアドレス。  
  
## 戻り値  
 エラーが発生した場合、または `E_FAIL` が成功した場合 `S_OK` 返します。  
  
## 解説  
 このメソッドは、`IOleWindow::GetWindow` メソッドに似ています。  
  
## 参照  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)