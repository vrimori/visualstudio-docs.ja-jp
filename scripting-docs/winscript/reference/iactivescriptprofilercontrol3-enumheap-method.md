---
title: Iactivescriptprofilercontrol 3::enumheap メソッド |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 2799d06d-20dd-4c12-9646-554c0ea3606e
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7d6fc79a9d6d35e35181c3505e07af2d9a1962c2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724562"
---
# <a name="iactivescriptprofilercontrol3enumheap-method"></a>IActiveScriptProfilerControl3::EnumHeap メソッド
インターフェイスを返します ([IActiveScriptProfilerHeapEnum インターフェイス](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)) を使用して、関連付けられているスクリプト エンジンのコンテキストで GC ヒープのオブジェクトを反復処理をすることができます。  
  
 デバッグ モードまたはリリース モードでこのメソッドを呼び出すことができます。 このメソッドは、UI スレッドがアイドル状態のときに呼び出す必要があります。 メソッドが呼び出された後の操作に対して実行してくださいありませんを除く、スクリプト エンジン[iactivescriptprofilerheapenum::next メソッド](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)まで[iactivescriptprofilerheapenum::next メソッド](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)S_FALSE を返しますまたは、 [IActiveScriptProfilerHeapEnum インターフェイス](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)インターフェイス ポインターを解放します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnumHeap([out] IActiveScriptProfilerHeapEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>パラメーター  
 ppEnum  
 [out]返します、 [IActiveScriptProfilerHeapEnum インターフェイス](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)です。  
  
## <a name="return-value"></a>戻り値  
 HRESULT。