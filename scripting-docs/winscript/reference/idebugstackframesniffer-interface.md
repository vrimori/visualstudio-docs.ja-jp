---
title: IDebugStackFrameSniffer インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrameSniffer interface
ms.assetid: 5669598e-a6bd-4694-9cb2-bd908be72bed
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 41fff384bc9075d94fcfa84d94350fec72ebc64a
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348881"
---
# <a name="idebugstackframesniffer-interface"></a>IDebugStackFrameSniffer インターフェイス
コンポーネントによって認識されている論理スタック フレームを列挙する手段を提供します。 スクリプト エンジンは、通常、このインターフェイスを実装します。 このインターフェイスのすべてのスタック フレームを検索するプロセス デバッグ マネージャーの使用は、特定のスレッドに関連付けられています。  
  
> [!NOTE]
>  デバッガーでは、関心のあるスレッド内からは、このインターフェイスを呼び出します。 スクリプト エンジンは、現在のスレッドを識別して、適切な列挙子を返す必要があります。  
  
## <a name="methods"></a>メソッド  
 継承されたメソッドだけでなく`IUnknown`、`IDebugStackFrameSniffer`インターフェイスは、次のメソッドを公開します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugStackFrameSniffer::EnumStackFrames](../../winscript/reference/idebugstackframesniffer-enumstackframes.md)|現在のスレッドのスタック フレームの列挙子を返します。|