---
title: IWebAppDiagnosticsSetup インターフェイス |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup Interface
ms.assetid: ec7359f2-633e-4d59-b64b-9cab0134dfd0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e273f29bee6e4d2aae26c01c477373a735624c8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734002"
---
# <a name="iwebappdiagnosticssetup-interface"></a>IWebAppDiagnosticsSetup インターフェイス
このインターフェイスは、PDM デバッグ アプリケーションは、デバッグ中のプロセスで COM オブジェクトを作成し、web の診断を有効にして実装されます。 場合は、PDM デバッグ アプリケーションのオブジェクトによって実装[IObjectWithSite](http://go.microsoft.com/fwlink/?LinkId=232438)、Internet Explorer を呼び出す[SetSite](http://go.microsoft.com/fwlink/?LinkId=232439)が作成された後、およびパスへの参照の[IWebBrowser2](http://go.microsoft.com/fwlink/?LinkId=232449). WWA アプリケーションから呼び出される[SetSite](http://go.microsoft.com/fwlink/?LinkId=232439)およびインターフェイス IWebApplicationHost の代わりに、WWA に渡します。 場合[SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) NULL 以外の値で呼び出されました[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)は true を返します。 場合は、false を返し、呼び出し[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)は失敗します。  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsSetup`PDM v11.0 以降によって実装されています。 activdbg100.h にあります。  
  
## <a name="methods"></a>メソッド  
 このインターフェイスは、次のメソッドを公開します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|指定したフィルターによって隠ぺいされているテキスト ドキュメントを取得します。|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|指定されたドキュメントがこのノードの子ノードのいずれかに属するかどうかを判断します。|