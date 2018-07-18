---
title: IDebugStackFrameSnifferEx インターフェイス |Microsoft ドキュメント
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
ms.openlocfilehash: 56d6e63c41db274634b2593989800ea0392b93a6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726762"
---
# <a name="idebugstackframesnifferex-interface"></a>IDebugStackFrameSnifferEx インターフェイス
コンポーネントによって把握されている論理スタック フレームを列挙する手段を提供します。 スクリプト エンジンは、通常、このインターフェイスを実装します。 このインターフェイスのすべてのスタック フレームを検索するデバッグ マネージャー使用の処理は、特定のスレッドに関連付けられています。  
  
> [!NOTE]
>  このインターフェイスは、目的のスレッド内からを呼び出されます。 インターフェイスの実装は、現在のスレッドを識別する必要があり、適切な列挙子を返します。  
  
 継承されたメソッドだけでなく`IDebugStackFrameSniffer`、`IDebugStackFrameSnifferEx`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugStackFrameSnifferEx::EnumStackFramesEx](../../winscript/reference/idebugstackframesnifferex-enumstackframesex.md)|現在のスレッドのスタック フレームの列挙子を返します。|