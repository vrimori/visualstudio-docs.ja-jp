---
title: IWebAppDiagnosticsSetup::DiagnosticsSupported |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup::DiagnosticsSupported
ms.assetid: 5bbcd0d0-1460-4cf7-bbb1-f4f4a04f739a
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df9296ac251d93105229fc0af365f6797a413f2b
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349687"
---
# <a name="iwebappdiagnosticssetupdiagnosticssupported"></a>IWebAppDiagnosticsSetup::DiagnosticsSupported
このアプリケーションでは診断がサポートされているかどうかを判断します。 場合[SetSite](http://go.microsoft.com/fwlink/?LinkId=232439)が NULL 以外の値では、このインターフェイスを実装するオブジェクトに対して呼び出された[DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)返します`true`します。 返されたそうでない場合は`false`への呼び出しと[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)失敗します。  
  
> [!IMPORTANT]
>  [IWebAppDiagnosticsSetup インターフェイス](../../winscript/reference/iwebappdiagnosticssetup-interface.md)PDM v11.0 以降によって実装された以降には。 Activdbg100 を記載されています。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DiagnosticsSupported(        [out, retval] VARIANT_BOOL* pRetVal        );  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 場合[SetSite](http://go.microsoft.com/fwlink/?LinkId=232439)が NULL 以外の値では、このインターフェイスを実装するオブジェクトに対して呼び出された[DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)返します`true`します。 返されたそうでない場合は`false`への呼び出しと[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)失敗します。