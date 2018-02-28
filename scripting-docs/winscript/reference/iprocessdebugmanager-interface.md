---
title: "IProcessDebugManager インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IProcessDebugManager interface
ms.assetid: b6ecb2bd-a4d1-4857-9232-036c154d0cb1
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26c97fda6fc8657164e22d51eb041017a6239d98
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iprocessdebugmanager-interface"></a>IProcessDebugManager インターフェイス
プロセスのデバッグ マネージャーをプライマリ インターフェイスです。 このインターフェイスは、作成、追加、またはプロセスから仮想アプリケーションを削除することができます。 スタック フレームとアプリケーションのスレッドを列挙します。  
  
 継承されたメソッドだけでなく`IUnknown`、`IProcessDebugManager`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IProcessDebugManager::CreateApplication](../../winscript/reference/iprocessdebugmanager-createapplication.md)|このアプリケーションの新しいデバッグ アプリケーション オブジェクトを作成します。|  
|[IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)|現在のプロセスの既定のアプリケーション オブジェクトを返します。|  
|[IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)|実行中のアプリケーションをマシン デバッグ マネージャーの一覧にアプリケーションを追加します。|  
|[IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)|実行中からアプリケーションを削除するアプリケーションの一覧です。|  
|[IProcessDebugManager::CreateDebugDocumentHelper](../../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md)|このアプリケーションの新しいデバッグ ドキュメント ヘルパーを作成します。|