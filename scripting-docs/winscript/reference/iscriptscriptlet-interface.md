---
title: "IScriptScriptlet インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IScriptScriptlet インターフェイス"
ms.assetid: b9981908-a337-4228-864c-c741f111ab2d
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IScriptScriptlet インターフェイス
インターフェイスの実装が `IScriptScriptlet` イベント ハンドラーのスクリプトを表すオブジェクト。  
  
 `IScriptEntry` から継承するメソッドに加え、`IScriptScriptlet` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IScriptScriptlet::GetEventName](../../winscript/reference/iscriptscriptlet-geteventname.md)|スクリプトレットに関連付けられたイベントの名前を返します。|  
|[IScriptScriptlet::GetSimpleEventName](../../winscript/reference/iscriptscriptlet-getsimpleeventname.md)|スクリプトレットに関連付けられている単純なイベントの名前を返します。  これは空白文字を含まない 1 語の名前です。|  
|[IScriptScriptlet::GetSubItemName](../../winscript/reference/iscriptscriptlet-getsubitemname.md)|スクリプトレットのオブジェクトのホストの完全修飾名の最後の識別子を返します。|  
|[IScriptScriptlet::SetEventName](../../winscript/reference/iscriptscriptlet-seteventname.md)|スクリプトレットに関連付けられたイベントの名前を設定します。|  
|[IScriptScriptlet::SetSimpleEventName](../../winscript/reference/iscriptscriptlet-setsimpleeventname.md)|スクリプトレットに関連付けられている単純なイベントの名前を設定します。  これは空白文字を含まない 1 語の名前です。|  
|[IScriptScriptlet::SetSubItemName](../../winscript/reference/iscriptscriptlet-setsubitemname.md)|スクリプトレットのオブジェクトのホストの完全修飾名の最後の識別子を設定します。|  
  
## 参照  
 [アクティブ スクリプト作成インターフェイス](../../winscript/reference/active-script-authoring-interfaces.md)