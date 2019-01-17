---
title: IActiveScriptDebug インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptDebug interface
ms.assetid: e3e28cba-ee08-4a52-973a-b74be488c348
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0e21f4c99da886bc4907acf8b0934e1b46d57689
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344578"
---
# <a name="iactivescriptdebug-interface"></a>IActiveScriptDebug インターフェイス
デバッグをサポートするスクリプト エンジンによって実装されます。 通常、実装するオブジェクト、`IActiveScriptDebug`インターフェイスの実装も、`IActiveScript`インターフェイス。 この場合は、呼び出し、`IActiveScript::QueryInterface`メソッドを取得する、`IActiveScriptDebug`インターフェイス。  
  
 `IActiveScriptDebug`インターフェイスにするための手段が用意されています。  
  
- ドキュメント管理を引き継ぐためのスマート ホスト。  
  
- 複数のスクリプト エンジンのデバッグを同期するプロセス デバッグ マネージャー。  
  
  継承されたメソッドだけでなく`IUnknown`、`IActiveScriptDebug`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)|スクリプトのテキストの任意のブロックのテキスト属性を返します。|  
|[IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)|任意のスクリプトレット テキスト属性を返します。|  
|[IActiveScriptDebug::EnumCodeContextsOfPosition](../../winscript/reference/iactivescriptdebug-enumcodecontextsofposition.md)|デリゲート`IDebugDocumentContext::EnumCodeContexts`します。|