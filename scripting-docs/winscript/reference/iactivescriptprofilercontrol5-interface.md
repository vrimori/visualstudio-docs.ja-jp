---
title: IActiveScriptProfilerControl5 インターフェイス |Microsoft ドキュメント
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
ms.openlocfilehash: e0c8b464004337b41280d6d19821f0fb9f1f50a5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724462"
---
# <a name="iactivescriptprofilercontrol5-interface"></a>IActiveScriptProfilerControl5 インターフェイス
スクリプト エンジンに関連付けられた GC ヒープ オブジェクトを列挙するメソッドを提供します。  
  
## <a name="syntax"></a>構文  
  
```  
interface IActiveScriptProfilerControl5 : IActiveScriptProfilerControl4  
```  
  
## <a name="methods"></a>メソッド  
 [IActiveScriptProfilerControl5::EnumHeap2 メソッド](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md)  
 インターフェイスを返します ([IActiveScriptProfilerHeapEnum インターフェイス](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)) を使用して、関連付けられているスクリプト エンジンのコンテキストで GC ヒープのオブジェクトを反復処理をすることができます。