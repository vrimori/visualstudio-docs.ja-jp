---
title: "IWebAppDiagnosticsSetup::DiagnosticsSupported |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IWebAppDiagnosticsSetup::DiagnosticsSupported
ms.assetid: 5bbcd0d0-1460-4cf7-bbb1-f4f4a04f739a
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5706d868f0096d486629c18c3d700349af92cc92
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iwebappdiagnosticssetupdiagnosticssupported"></a>IWebAppDiagnosticsSetup::DiagnosticsSupported
このアプリケーションに診断がサポートされているかどうかを判断します。 場合[SetSite](http://go.microsoft.com/fwlink/?LinkId=232439)は NULL 以外の値を持つには、このインターフェイスを実装するオブジェクトで呼び出されて[DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)返します`true`です。 Not、返された場合`false`への呼び出しと[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)は失敗します。  
  
> [!IMPORTANT]
>  [IWebAppDiagnosticsSetup インターフェイス](../../winscript/reference/iwebappdiagnosticssetup-interface.md)は、PDM v11.0 以降によって実装されている値を超えています。 Activdbg100 で見つかりました。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DiagnosticsSupported(        [out, retval] VARIANT_BOOL* pRetVal        );  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 場合[SetSite](http://go.microsoft.com/fwlink/?LinkId=232439)は NULL 以外の値を持つには、このインターフェイスを実装するオブジェクトで呼び出されて[DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)返します`true`です。 Not、返された場合`false`への呼び出しと[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)は失敗します。