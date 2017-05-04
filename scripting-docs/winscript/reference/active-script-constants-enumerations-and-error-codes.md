---
title: "アクティブ スクリプトの定数、列挙型、およびエラー コード | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: aab24471-5817-45c0-be07-ffe4648923ed
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# アクティブ スクリプトの定数、列挙型、およびエラー コード
ここでは、Windows のスクリプト エンジンで使用される列挙体、およびエラー コードを記述します。  
  
## 定数  
  
|定数|説明|  
|--------|--------|  
|[SCRIPTTHREADID 定数](../../winscript/reference/scriptthreadid-constants.md)|スレッドの種類を指定します。|  
  
## プロパティ  
  
|プロパティ|説明|  
|-----------|--------|  
|[SCRIPTPROP\_HOSTKEEPALIVE プロパティ](../../winscript/reference/scriptprop-hostkeepalive-property.md)|未解決の参照がある場合は、スクリプト エンジンが十分に機能して保存するかどうかを指定するために使用します。|  
  
## 列挙型  
  
|列挙型|説明|  
|---------|--------|  
|[SCRIPTGCTYPE 列挙型](../../winscript/reference/scriptgctype-enumeration.md)|実行するガベージ コレクションの種類。|  
|[SCRIPTLANGUAGEVERSION 列挙型](../../winscript/reference/scriptlanguageversion-enumeration.md)|可能なスクリプト バージョンを指定します。|  
|[SCRIPTSTATE 列挙型](../../winscript/reference/scriptstate-enumeration.md)|スクリプト エンジンの状態を指定します。|  
|||  
|[SCRIPTTHREADSTATE 列挙型](../../winscript/reference/scriptthreadstate-enumeration.md)|スクリプト エンジンでスレッドの状態を指定します。|  
|[SCRIPTTRACEINFO 列挙型](../../winscript/reference/scripttraceinfo-enumeration.md)|トレースするスクリプトのイベントを表します。  [IActiveScriptSiteTraceInfo::SendScriptTraceInfo メソッド](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md)で使用します。|  
|[SCRIPTUICHANDLING 列挙型](../../winscript/reference/scriptuichandling-enumeration.md)|処理される UI コントロールを配置する方法を表します。|  
|[SCRIPTUICITEM 列挙型](../../winscript/reference/scriptuicitem-enumeration.md)|UI 項目の種類を表します。  [IActiveScriptSiteUIControl::GetUIBehavior メソッド](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md)で使用します。|  
  
## エラー コード  
  
|エラー コード|説明|  
|-------------|--------|  
|[SCRIPT\_E\_PROPAGATE エラー コード](../../winscript/reference/script-e-propagate-error-code.md)|スクリプト エラーは別のスレッドにある呼び出し元に広められています。|  
|[SCRIPT\_E\_RECORDED エラー コード](../../winscript/reference/script-e-recorded-error-code.md)|エラーは、スクリプト エンジンとホストの間に渡されました。|  
|[SCRIPT\_E\_REPORTED エラー コード](../../winscript/reference/script-e-reported-error-code.md)|スクリプト エンジンは、ホストにハンドルされない例外が発生しました。|  
  
## 参照  
 [アクティブ スクリプト インターフェイス](../../winscript/reference/active-script-interfaces.md)