---
title: "IDebugSessionProviderEx インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 26c5da2d-8c93-4d2b-94d2-97aaa377dcfe
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugSessionProviderEx インターフェイス
主インターフェイスは、デバッガーの IDE によってホストを有効にするために提供され、デバッグを言語に取り組んでいます。  これは実行中のアプリケーションのデバッグ セッションを設定します。  このインターフェイスは、コンピューターのデバッグ マネージャーによって実装されます。  
  
 `IUnknown` から継承するメソッドに加え、`IDebugSessionProviderEx` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IDebugSessionProviderEx:CanJITDebug](../../winscript/reference/idebugsessionproviderex-canjitdebug.md)|デバッグ時には、指定したアプリケーションと可能かどうかを判定します。|  
|[IDebugSessionProviderEx:StartDebugSession](../../winscript/reference/idebugsessionproviderex-startdebugsession.md)|指定したアプリケーションのデバッグ セッションを開始します。|