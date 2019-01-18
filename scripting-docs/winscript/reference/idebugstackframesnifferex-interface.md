---
title: IDebugStackFrameSnifferEx インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrameSnifferEx interface
ms.assetid: fd6cf744-dee7-45f2-9a90-355b90372923
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76f10d6bbb34c61e87a1be0f61dcd7db168274e7
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348491"
---
# <a name="idebugstackframesnifferex-interface"></a>IDebugStackFrameSnifferEx インターフェイス
コンポーネントによって認識されている論理スタック フレームを列挙する手段を提供します。 スクリプト エンジンは、通常、このインターフェイスを実装します。 このインターフェイスのすべてのスタック フレームを検索するプロセス デバッグ マネージャーの使用は、特定のスレッドに関連付けられています。  
  
> [!NOTE]
>  このインターフェイスは、関心のあるスレッド内からを呼び出されます。 インターフェイスの実装は、現在のスレッドを識別して、適切な列挙子を返す必要があります。  
  
 継承されたメソッドだけでなく`IDebugStackFrameSniffer`、`IDebugStackFrameSnifferEx`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugStackFrameSnifferEx::EnumStackFramesEx](../../winscript/reference/idebugstackframesnifferex-enumstackframesex.md)|現在のスレッドのスタック フレームの列挙子を返します。|