---
title: "IProcessDebugManager インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IProcessDebugManager インターフェイス"
ms.assetid: b6ecb2bd-a4d1-4857-9232-036c154d0cb1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProcessDebugManager インターフェイス
プロセス デバッグ マネージャーへの主要なインターフェイス。  このインターフェイスは、プロセスから仮想アプリケーションを作成するか、追加、または削除できます。  これは、スタック フレームとアプリケーションのスレッドを列挙できます。  
  
 `IUnknown` から継承するメソッドに加え、`IProcessDebugManager` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IProcessDebugManager::CreateApplication](../../winscript/reference/iprocessdebugmanager-createapplication.md)|このアプリケーションの新しいデバッグ アプリケーション オブジェクトを作成します。|  
|[IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)|現在のプロセスの既定のアプリケーション オブジェクトを返します。|  
|[IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)|コンピューターのデバッグ マネージャーの実行中のアプリケーションのリストにアプリケーションが追加されます。|  
|[IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)|実行中のアプリケーションの一覧からアプリケーションを削除します。|  
|[IProcessDebugManager::CreateDebugDocumentHelper](../../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md)|このアプリケーションのデバッグ ヘルパーの新しいドキュメントを作成します。|