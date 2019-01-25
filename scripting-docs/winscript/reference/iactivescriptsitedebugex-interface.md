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
ms.openlocfilehash: e390b610d6912de0078b817c9dfb503e5924a374
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54797430"
---
# <a name="iactivescriptsitedebugex-interface"></a>IActiveScriptSiteDebugEx インターフェイス

と共にこのインターフェイスを実装、`IActiveScriptSiteDebug`インターフェイスのアプリケーションで、実行時エラーの通知を取得し、必要に応じて、デバッグ用のアプリケーションにアタッチする必要があるホストを作成する場合。 プロセス デバッグ マネージャーを介して通知を提供する`IActiveScriptDebug`時での Just スクリプト デバッガーの場合は、コンピューターに存在します。 ジャスト イン タイムにスクリプト デバッガーがない場合は、見つかると、PDM を介して通知を提供する`IActiveScriptDebugEx`代わりにします。

実行時エラーの通知を取得する、ホストで処理する必要があります`ActiveScriptSiteDebug::OnScriptErrorDebug`します。 ユーザー操作に基づいて、し、かどうかに返された場合、内部デバッガーをアタッチするか、OnScriptErrorDebug のデバッガーの起動を返す`pfEnterDebugger`パラメーター。

## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド

|メソッド|説明|
|------------|-----------------|
|[IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug](../../winscript/reference/iactivescriptsitedebugex-oncannotjitscripterrordebug.md)|プロセス デバッグ マネージャーとは、スクリプト実行時のエラーについて、ホストには、外部の Just In Time デバッガーが見つからないことを通知します。|