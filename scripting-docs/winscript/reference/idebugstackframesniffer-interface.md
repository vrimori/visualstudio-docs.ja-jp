---
title: "IDebugStackFrameSniffer インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrameSniffer interface
ms.assetid: 5669598e-a6bd-4694-9cb2-bd908be72bed
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 250c104d24f27900a6ff0eb8e8f72644f820bf5a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframesniffer-interface"></a>IDebugStackFrameSniffer インターフェイス
コンポーネントによって把握されている論理スタック フレームを列挙する手段を提供します。 スクリプト エンジンは、通常、このインターフェイスを実装します。 このインターフェイスのすべてのスタック フレームを検索するデバッグ マネージャー使用の処理は、特定のスレッドに関連付けられています。  
  
> [!NOTE]
>  デバッガーは、目的のスレッド内からは、このインターフェイスを呼び出します。 スクリプト エンジンは、現在のスレッドを識別する必要があり、適切な列挙子を返します。  
  
## <a name="methods"></a>メソッド  
 継承されたメソッドだけでなく`IUnknown`、`IDebugStackFrameSniffer`インターフェイスは、次のメソッドを公開します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugStackFrameSniffer::EnumStackFrames](../../winscript/reference/idebugstackframesniffer-enumstackframes.md)|現在のスレッドのスタック フレームの列挙子を返します。|