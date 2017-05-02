---
title: "IRemoteDebugApplication110 インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IRemoteDebugApplication110 インターフェイス"
ms.assetid: 785ab46a-8827-41cb-806a-132e6b2c8f47
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IRemoteDebugApplication110 インターフェイス
スクリプト デバッガーとインプロセス呼び出し元から呼び出すことができる新しい機能を提供するために使用します。  
  
> [!IMPORTANT]
>  このインターフェイスは PDM v11.0 を超えるによって実装されます。  activdbg100.h.である。  
  
## メソッド  
 `IRemoteDebugApplication110` インターフェイスは、以下のメソッドを公開します。  
  
|メソッド|説明|  
|----------|--------|  
|[IRemoteDebugApplication110::SetDebuggerOptions](../../winscript/reference/iremotedebugapplication110-setdebuggeroptions.md)|デバッガー オプションを更新するために呼び出されます。  オプションは 0 になります \(SDO\_NONE\)。|  
|[IRemoteDebugApplication110::GetCurrentDebuggerOptions](../../winscript/reference/iremotedebugapplication110-getcurrentdebuggeroptions.md)|有効なオプションの現在のセットを返します。|  
|[IRemoteDebugApplication110::GetMainThread](../../winscript/reference/iremotedebugapplication110-getmainthread.md)|SetSite を呼び出すホストのメイン スレッドを返します。|