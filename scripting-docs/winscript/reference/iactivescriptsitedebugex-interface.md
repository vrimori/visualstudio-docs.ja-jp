---
title: IActiveScriptSiteDebugEx インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteDebugEx Interface
ms.assetid: 76869378-1a7b-47bd-8cd0-acc31f91d58d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c1e462630f7bf52c4ca94aa59df22616e9a335a7
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345878"
---
# <a name="iactivescriptsitedebugex-interface"></a>IActiveScriptSiteDebugEx インターフェイス
と共にこのインターフェイスを実装、`IActiveScriptSiteDebug`インターフェイスのアプリケーションで、実行時エラーの通知を取得し、必要に応じて、デバッグ用のアプリケーションにアタッチする必要があるホストを作成する場合。 プロセス デバッグ マネージャーを介して通知を提供する`IActiveScriptDebug`時での Just スクリプト デバッガーの場合は、コンピューターに存在します。 ジャスト イン タイムにスクリプト デバッガーがない場合は、見つかると、PDM を介して通知を提供する`IActiveScriptDebugEx`代わりにします。  
  
 実行時エラーの通知を取得する、ホストで処理する必要があります[ActiveScriptSiteDebug::OnScriptErrorDebug](http://msdn.microsoft.com/en-us/cf7639f9-a699-4571-9f3a-82ef52c0b5f4)します。 ユーザー操作に基づいて、し、かどうかに返された場合、内部デバッガーをアタッチするか、OnScriptErrorDebug のデバッガーの起動を返す`pfEnterDebugger`パラメーター。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug](../../winscript/reference/iactivescriptsitedebugex-oncannotjitscripterrordebug.md)|プロセス デバッグ マネージャーとは、スクリプト実行時のエラーについて、ホストには、外部の Just In Time デバッガーが見つからないことを通知します。|