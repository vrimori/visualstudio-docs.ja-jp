---
title: "IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp"
ms.assetid: 30975973-acb1-48f4-8266-5e097a57db22
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
このメソッドは、ID を `dwClsContext`を使用して `rclsid` に渡すクラスを共同作成します。  これは [IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md) の動作が、`CreateObjectWithSiteAtWebApp` の場合はオブジェクトは、Web アプリケーションの UI スレッドで非同期的に作成される方法に似ています。  クラス ID で指定されたオブジェクトは [IWebAppDiagnosticsObjectInitialization インターフェイス](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md)を実装する必要があります。  オブジェクトが作成されると、[IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) は `CreateObjectWithSiteAtWebApp`の PDM のデバッグ アプリケーションと `hPassToObject` のパラメーターへの参照と呼ばれます。  コピー [DuplicateHandle](http://go.microsoft.com/fwlink/?LinkId=232450)匿名パイプにアプリケーションへのハンドルを渡すには、このメソッドを使用できます。  
  
> [!IMPORTANT]
>  [IWebAppDiagnosticsSetup インターフェイス](../../winscript/reference/iwebappdiagnosticssetup-interface.md) は PDM v11.0 を超えるによって実装されます。  activdbg100.h.である。  
  
## 構文  
  
```cpp  
HRESULT CreateObjectWithSiteAtWebApp(  
        [in] REFCLSID rclsid,   
        [in] DWORD dwClsContext,   
        [in] REFIID riid,   
        [in] DWORD_PTR hPassToObject  
        );  
  
```  
  
#### パラメーター  
 `rclsid`  
 作成するクラスのクラス ID。  
  
 `dwClsContext`  
 コードが実行されるコンテキスト。  多くの場合、は CLSCTX\_INPROC\_SERVER です。  
  
 `riid`  
 使用しません。  
  
 `hPassToObject`  
 オブジェクトには、一度に渡される値は、UI スレッドでオブジェクトが [IWebAppDiagnosticsObjectInitialization インターフェイス](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md)を実装する場合は、作成されます。