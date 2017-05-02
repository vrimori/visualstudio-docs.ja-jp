---
title: "IWebAppDiagnosticsObjectInitialization::Initialize | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IWebAppDiagnosticsObjectInitialization::Initialize"
ms.assetid: 7ccfac28-9f65-4e1c-a0fb-a8a6c7f75b63
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IWebAppDiagnosticsObjectInitialization::Initialize
[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)で作成されたオブジェクトの初期化。  
  
> [!IMPORTANT]
>  [IWebAppDiagnosticsObjectInitialization インターフェイス](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md) は activdbg100.h.にあります。  
  
## 構文  
  
```cpp  
HRESULT Initialize(  
        [in, annotation("__in")] HANDLE_PTR hPassedHandle,  
        [in, annotation("__in")] IUnknown* pDebugApplication  
        );  
```  
  
#### パラメーター  
 `hPassedHandle`  
 `hPassToObject` のパラメーターの [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) のメソッドに渡されたハンドル。  
  
 `pDebugApplication`  
 オブジェクトが作成された PDM アプリケーション。