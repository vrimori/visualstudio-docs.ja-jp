---
title: "IActiveScriptSiteWindow | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptSiteWindow インターフェイス"
ms.assetid: 96d5c493-2c0b-47e2-848b-4a8dacdcd65c
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSiteWindow
このインターフェイスは [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) と同じオブジェクトのユーザー インターフェイスをサポートするホストによって実装されます。  ユーザー インターフェイスを、サーバーなど、サポートしないホストは、`IActiveScriptSiteWindow` のインターフェイスを実装しません。  スクリプト エンジンは `IActiveScriptSite`から `QueryInterface` を呼び出して、このインターフェイスへのアクセス。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IActiveScriptSiteWindow::GetWindow](../../winscript/reference/iactivescriptsitewindow-getwindow.md)|表示するスクリプト エンジンがあるポップアップ ウィンドウのオーナーとして機能するウィンドウ ハンドルを取得します。|  
|[IActiveScriptSiteWindow::EnableModeless](../../winscript/reference/iactivescriptsitewindow-enablemodeless.md)|ホストをメイン ウィンドウ、またはモードレス ダイアログ ボックスを有効または無効にします。|  
  
## 参照  
 [アクティブ スクリプト インターフェイス](../../winscript/reference/active-script-interfaces.md)