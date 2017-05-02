---
title: "IWebAppDiagnosticsSetup インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IWebAppDiagnosticsSetup インターフェイス"
ms.assetid: ec7359f2-633e-4d59-b64b-9cab0134dfd0
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IWebAppDiagnosticsSetup インターフェイス
このインターフェイスは、デバッグ作成し、Web 診断を実装するプロセスの COM オブジェクトを有効にする PDM のデバッグ アプリケーションで。  PDM のデバッグ アプリケーション オブジェクト [IObjectWithSite](http://go.microsoft.com/fwlink/?LinkId=232438)がを実装する、Internet Explorer の呼び出し [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) に [IWebBrowser2](http://go.microsoft.com/fwlink/?LinkId=232449)作成され、参照に合格したら。  WWA の WWA アプリケーションの呼び出し [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) とパスが IWebApplicationHost を実装します。  [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) null 以外の値があった場合、[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) は true を返します。  でない場合は、false を返し、[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) への呼び出しは失敗します。  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsSetup` は PDM v11.0 を超えるによって実装されます。  activdbg100.h.である。  
  
## メソッド  
 このインターフェイスは、次にメソッドを公開します。  
  
|メソッド|説明|  
|----------|--------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|指定したフィルターによって非表示になっているテキスト ドキュメントを取得します。|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|指定されたドキュメントがこのノードの子ノードの 1 に属するかどうかを判断します。|