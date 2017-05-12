---
title: "IActiveScript | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScript インターフェイス"
ms.assetid: d8acee11-7f0d-4999-b97a-66774af16f71
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript
スクリプト エンジンの初期化に必要なメソッドが用意されています。  スクリプト エンジンは `IActiveScript` のインターフェイスを実装する必要があります。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)|ホストによって提供される [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) のサイトをスクリプト エンジンに通知します。|  
|[IActiveScript::GetScriptSite](../../winscript/reference/iactivescript-getscriptsite.md)|Windows のスクリプト エンジンに関連付けられたサイトのオブジェクトを取得します。|  
|[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)|指定された状態にスクリプト エンジンを設定します。|  
|[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)|スクリプト エンジンの現在の状態を取得します。|  
|[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)|したがって、スクリプト エンジンを現在読み込まれているスクリプトを破棄し、状態を失い、によって他のオブジェクトのインターフェイス ポインターを解放するためにを呼び出した場合、終了済みの状態になります。|  
|[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)|スクリプト エンジンの名前空間にルート レベルの名前を追加します。|  
|[IActiveScript::AddTypeLib](../../winscript/reference/iactivescript-addtypelib.md)|スクリプトの名前空間にタイプ ライブラリを追加します。|  
|[IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)|実行中のスクリプトの `IDispatch` のインターフェイスを取得します。|  
|[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)|現在実行しているスレッドのスクリプト エンジンを書き直して定義済み識別子を取得します。|  
|[IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)|Microsoft Win32 の特定のスレッドに関連付けられているスレッドのスクリプト エンジンを書き直して定義済み識別子を取得します。|  
|[IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)|スクリプトのスレッドの現在の状態を取得します。|  
|[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)|実行中のスクリプトのスレッドで実行を中断します。|  
|[IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)|現在のスレッドでサイトを持たない読み込まれたスクリプト エンジンが返す現在のスクリプト エンジン \(すべての現在の実行状態プラス\) 複製します。|  
  
## 参照  
 [Windows スクリプト インターフェイスのリファレンス](../../winscript/reference/windows-script-interfaces-reference.md)