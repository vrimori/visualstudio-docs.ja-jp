---
title: "IActiveScriptWinRTErrorDebug インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptWinRTErrorDebug インターフェイス"
ms.assetid: 58b45096-633f-479f-95c4-8eae7376d3a1
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IActiveScriptWinRTErrorDebug インターフェイス
[BREAKREASON 列挙型](../../winscript/reference/breakreason-enumeration.md) のイベントから拡張 Windows のランタイム エラー情報を提供する JavaScript エンジンによって実装されます。  [IActiveScriptError](../../winscript/reference/iactivescripterror.md) のオブジェクトからの派生に QueryInterface をできます。  
  
> [!IMPORTANT]
>  このインターフェイスは PDM v11.0 を超えるによって実装されます。  activdbg100.h.である。  
  
## メソッド  
 `IActiveScriptWinRTErrorDebug` インターフェイスは、以下のメソッドを公開します。  
  
|メソッド|説明|  
|----------|--------|  
|[IActiveScriptWinRTErrorDebug::GetCapabilitySid](../../winscript/reference/iactivescriptwinrterrordebug-getcapabilitysid.md)|Windows のランタイム エラーの機能の SID を、可能であれば返します。|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorreference.md)|Windows のランタイムの制限されたエラーの参照の文字列を、可能であれば返します。|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorString](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorstring.md)|Windows のランタイムによって制限されるエラー文字列を、可能であれば返します。|