---
title: "SCRIPT_DEBUGGER_OPTIONS 列挙型 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "SCRIPT_DEBUGGER_OPTIONS 列挙型"
ms.assetid: aef41ec0-6f65-48e8-a69e-44b4e4fb929f
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# SCRIPT_DEBUGGER_OPTIONS 列挙型
アタッチされたデバッガーに適用する機能や、一連のオプションを示します。  [IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) およびで使用される [IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
>  これらの定数は PDM v10.0 を超えるによって実装されます。  activdbg100.h.である。  
  
## 構文  
  
```  
typedef SCRIPT_DEBUGGER_OPTIONS  
```  
  
## メンバー  
  
|メンバー|値|説明|  
|----------|-------|--------|  
|SDO\_NONE|0x00000000|オプションは設定されていません。|  
|SDO\_ENABLE\_FIRST\_CHANCE\_EXCEPTIONS|0x00000001|例外がスローされたときにスクリプトのランタイムが BREAKREASON\_ERROR のイベントを発生させる必要があることを示します。  このオプションは、ユーザー コードで、または `Debug.enableFirstChanceExceptions(<true&#124;false>)`デバッガーによってセットによって設定される場合があります。|  
|SDO\_ENABLE\_WEB\_WORKER\_SUPPORT|0x00000002|デバッガーがアタッチされた Web ワーカー スレッドをサポートすることを示します。|  
  
## 参照  
 [アクティブ スクリプト デバッガーの定数、列挙型、および構造体](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)