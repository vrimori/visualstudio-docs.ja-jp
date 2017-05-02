---
title: "IWebAppDiagnosticsObjectInitialization インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IWebAppDiagnosticsObjectInitialization インターフェイス"
ms.assetid: 32847838-01d9-4205-a811-3043d8c7a917
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IWebAppDiagnosticsObjectInitialization インターフェイス
このインターフェイスは [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)を実装するクラスに実装できます。  [IWebAppDiagnosticsSetup インターフェイス](../../winscript/reference/iwebappdiagnosticssetup-interface.md) は、オブジェクトによって実装する [IDebugApplication インターフェイス](../../winscript/reference/idebugapplication-interface.md)実行されます。  ほとんどの場合、このオブジェクトは PDM です。  
  
 オブジェクトが作成されると、[IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) は `CreateObjectWithSiteAtWebApp`の PDM のデバッグ アプリケーションと `hPassToObject` のパラメーターへの参照と呼ばれます。  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsObjectInitialization` は activdbg100.h.にあります。  
  
## メソッド  
 このインターフェイスは、次にメソッドを公開します。  
  
|メソッド|説明|  
|----------|--------|  
|[IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md)|オブジェクトを初期化します。|