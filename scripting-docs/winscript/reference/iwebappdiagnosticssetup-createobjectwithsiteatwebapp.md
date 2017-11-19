---
title: "IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
ms.assetid: 30975973-acb1-48f4-8266-5e097a57db22
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1442297fcacb3a9464f9ea67489c91c8ab64ad78
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iwebappdiagnosticssetupcreateobjectwithsiteatwebapp"></a>IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
このメソッドは、クラス内で渡す ID を持つを共同作成`rclsid`を使用して、`dwClsContext`です。 これは、方法に似ています[IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md)ことの場合を除いて、動作`CreateObjectWithSiteAtWebApp`オブジェクトは、web アプリケーションの UI スレッドで非同期的に作成します。 クラス ID で指定されたオブジェクトを実装する必要があります[IWebAppDiagnosticsObjectInitialization インターフェイス](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md)です。 オブジェクトが作成された後[IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md)が PDM デバッグ アプリケーションへの参照で呼び出されると、`hPassToObject`のパラメーター`CreateObjectWithSiteAtWebApp`です。 このメソッドを使用するには、アプリへのハンドルを使用してコピーした匿名パイプに渡す[:duplicatehandle](http://go.microsoft.com/fwlink/?LinkId=232450)です。  
  
> [!IMPORTANT]
>  [IWebAppDiagnosticsSetup インターフェイス](../../winscript/reference/iwebappdiagnosticssetup-interface.md)は、PDM v11.0 以降によって実装されている値を超えています。 activdbg100.h にあります。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateObjectWithSiteAtWebApp(        [in] REFCLSID rclsid,         [in] DWORD dwClsContext,         [in] REFIID riid,         [in] DWORD_PTR hPassToObject        );  
```  
  
#### <a name="parameters"></a>パラメーター  
 `rclsid`  
 作成するクラスのクラス ID。  
  
 `dwClsContext`  
 コードを実行するコンテキスト。 ほとんどの場合は、CLSCTX_INPROC_SERVER を勧めします。  
  
 `riid`  
 使用しません。  
  
 `hPassToObject`  
 渡されるオブジェクトは、UI スレッドで、作成後、オブジェクトを実装する場合を値[IWebAppDiagnosticsObjectInitialization インターフェイス](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md)です。