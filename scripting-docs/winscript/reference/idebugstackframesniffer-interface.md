---
title: "IDebugStackFrameSniffer インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugStackFrameSniffer インターフェイス"
ms.assetid: 5669598e-a6bd-4694-9cb2-bd908be72bed
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrameSniffer インターフェイス
コンポーネントによって認識される論理スタック フレームを列挙する方法を示します。  スクリプト エンジンは通常、このインターフェイスを実装します。  プロセス デバッグ マネージャーは、特定のスレッドに関連付けられたすべてのスタック フレームを検索するには、このインターフェイスを使用します。  
  
> [!NOTE]
>  デバッガーは、対象スレッド内でこのインターフェイスを呼び出します。  スクリプト エンジンは、現在のスレッドを識別し、適切な列挙子を返す必要があります。  
  
## メソッド  
 `IUnknown` から継承するメソッドに加え、`IDebugStackFrameSniffer` インターフェイスは次のメソッドを公開します。  
  
|メソッド|説明|  
|----------|--------|  
|[IDebugStackFrameSniffer::EnumStackFrames](../../winscript/reference/idebugstackframesniffer-enumstackframes.md)|現在のスレッドのスタック フレームの列挙子を返します。|