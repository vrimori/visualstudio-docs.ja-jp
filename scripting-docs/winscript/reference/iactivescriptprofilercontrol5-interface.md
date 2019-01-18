---
title: IActiveScriptProfilerControl5 インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 7fd0ce34-6ae3-428f-ba90-3e86a8a98ed0
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b20afd05116a98e81a3eeea82e83e6ed200c44a
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349284"
---
# <a name="iactivescriptprofilercontrol5-interface"></a>IActiveScriptProfilerControl5 インターフェイス
スクリプト エンジンに関連付けられた GC ヒープ オブジェクトを列挙するメソッドを提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp
interface IActiveScriptProfilerControl5 : IActiveScriptProfilerControl4  
```  
  
## <a name="methods"></a>メソッド  
 [IActiveScriptProfilerControl5::EnumHeap2 メソッド](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md)  
 インターフェイスを返します ([IActiveScriptProfilerHeapEnum インターフェイス](../../winscript/reference/iactivescriptprofilerheapenum-interface.md))、関連付けられているスクリプト エンジンのコンテキストで GC ヒープ オブジェクトを反復処理に使用できます。