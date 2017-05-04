---
title: "IDebugStackFrameSnifferEx インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugStackFrameSnifferEx インターフェイス"
ms.assetid: fd6cf744-dee7-45f2-9a90-355b90372923
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrameSnifferEx インターフェイス
コンポーネントによって認識される論理スタック フレームを列挙する方法を示します。  スクリプト エンジンは通常、このインターフェイスを実装します。  プロセス デバッグ マネージャーは、特定のスレッドに関連付けられたすべてのスタック フレームを検索するには、このインターフェイスを使用します。  
  
> [!NOTE]
>  このインターフェイスは、対象スレッド内から呼び出されます。  インターフェイスの実装では、現在のスレッドを識別し、適切な列挙子を返す必要があります。  
  
 `IDebugStackFrameSniffer` から継承するメソッドに加え、`IDebugStackFrameSnifferEx` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IDebugStackFrameSnifferEx::EnumStackFramesEx](../../winscript/reference/idebugstackframesnifferex-enumstackframesex.md)|現在のスレッドのスタック フレームの列挙子を返します。|