---
title: "IActiveScript |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScript interface
ms.assetid: d8acee11-7f0d-4999-b97a-66774af16f71
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68d91a7ad91364d0c2133150d76cdb221929b16b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescript"></a>IActiveScript
スクリプト エンジンを初期化するために必要なメソッドを提供します。 スクリプト エンジンを実装する必要があります、`IActiveScript`インターフェイスです。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)|スクリプト エンジンに通知、 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)サイトにホストによって提供されます。|  
|[IActiveScript::GetScriptSite](../../winscript/reference/iactivescript-getscriptsite.md)|Windows スクリプト エンジンに関連付けられているサイト オブジェクトを取得します。|  
|[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)|指定した状態に、スクリプト エンジンを配置します。|  
|[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)|スクリプト エンジンの現在の状態を取得します。|  
|[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)|現在読み込まれているスクリプトの破棄の状態が失われるおよびその他のオブジェクトは、したがって closed の状態を入力する必要があるインターフェイス ポインターを解放するには、スクリプト エンジンが発生します。|  
|[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)|スクリプト エンジンの名前空間には、ルート レベルの項目の名前を追加します。|  
|[IActiveScript::AddTypeLib](../../winscript/reference/iactivescript-addtypelib.md)|スクリプトの名前空間をタイプ ライブラリを追加します。|  
|[IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)|取得、`IDispatch`実行中のスクリプトのインターフェイスです。|  
|[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)|現在実行中のスレッドのスクリプト エンジン定義の識別子を取得します。|  
|[IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)|特定の Microsoft Win32 スレッドに関連付けられているスレッドのスクリプト エンジン定義の識別子を取得します。|  
|[IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)|スクリプトのスレッドの現在の状態を取得します。|  
|[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)|スクリプトの実行中のスレッドの実行を中断します。|  
|[IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)|現在のスクリプト エンジン (すべて現在の実行状態)、マイナス記号を現在のスレッド内のサイトを持たない読み込まれたスクリプト エンジンを返すのクローンを作成します。|  
  
## <a name="see-also"></a>関連項目  
 [Windows スクリプト インターフェイスのリファレンス](../../winscript/reference/windows-script-interfaces-reference.md)