---
title: "IDebugSessionProvider インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugSessionProvider インターフェイス"
ms.assetid: 1b898423-7af9-44f5-8dda-987005309c99
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSessionProvider インターフェイス
ホストと言語を有効にするために、デバッガー IDE によって提供されるプライマリ インターフェイスは、デバッグで。  これは実行中のアプリケーションのデバッグ セッションを設定します。  このインターフェイスは、コンピューターのデバッグ マネージャーによって実装されます。  
  
 `IUnknown` から継承するメソッドに加え、`IDebugSessionProvider` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IDebugSessionProvider::StartDebugSession](../../winscript/reference/idebugsessionprovider-startdebugsession.md)|指定したアプリケーションのデバッグ セッションを開始します。|