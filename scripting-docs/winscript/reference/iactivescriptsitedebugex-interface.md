---
title: "IActiveScriptSiteDebugEx インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteDebugEx Interface
ms.assetid: 76869378-1a7b-47bd-8cd0-acc31f91d58d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2cf5849ff1fca282bace97774c6b7ac9e4510226
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebugex-interface"></a>IActiveScriptSiteDebugEx インターフェイス
と共にこのインターフェイスを実装して、`IActiveScriptSiteDebug`インターフェイスのアプリケーションの実行時エラーの通知を取得し、必要に応じて、デバッグ用のアプリケーションにアタッチする必要があるホストを作成している場合。 プロセスをデバッグ マネージャーを使用して通知を提供する`IActiveScriptDebug`ジャスト イン タイム スクリプト デバッガーが見つからない場合は、コンピューターにします。 ジャスト イン タイム スクリプト デバッガーがない場合は、PDM 提供を通じて通知`IActiveScriptDebugEx`代わりにします。  
  
 実行時エラーの通知を取得するには、ホストが処理する必要があります[ActiveScriptSiteDebug::OnScriptErrorDebug](http://msdn.microsoft.com/en-us/cf7639f9-a699-4571-9f3a-82ef52c0b5f4)です。 ユーザー操作に基づいて、し、かどうかを戻り値、内部のデバッガーを添付する、またはを返す、OnScriptErrorDebug でデバッガーの起動`pfEnterDebugger`パラメーター。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug](../../winscript/reference/iactivescriptsitedebugex-oncannotjitscripterrordebug.md)|プロセス マネージャーをデバッグするときに、スクリプト実行時のエラーについて、ホストには、外部のときにだけデバッガーが見つからないに通知します。|