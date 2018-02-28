---
title: "IWebAppDiagnosticsObjectInitialization インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsObjectInitialization Interface
ms.assetid: 32847838-01d9-4205-a811-3043d8c7a917
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 159b81a336accea4e4e8c035119d5525de71ae90
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iwebappdiagnosticsobjectinitialization-interface"></a>IWebAppDiagnosticsObjectInitialization インターフェイス
このインターフェイスを実装するクラスで実装できます[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)です。 [IWebAppDiagnosticsSetup インターフェイス](../../winscript/reference/iwebappdiagnosticssetup-interface.md)を実装するオブジェクトによって実装される[IDebugApplication インターフェイス](../../winscript/reference/idebugapplication-interface.md)です。 ほとんどの場合は、このオブジェクトは、PDM は。  
  
 オブジェクトが作成された後[IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md)が PDM デバッグ アプリケーションへの参照で呼び出されると、`hPassToObject`のパラメーター`CreateObjectWithSiteAtWebApp`です。  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsObjectInitialization`activdbg100.h に存在します。  
  
## <a name="methods"></a>メソッド  
 このインターフェイスは、次のメソッドを公開します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md)|オブジェクトを初期化します。|