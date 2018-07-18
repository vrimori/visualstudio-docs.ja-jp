---
title: IActiveScriptProfilerControl3 インターフェイス |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 64bc860a-54d4-475a-80f6-2f9dba6448ee
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eed00579acfb09217183a1dd1d858a1e99257a2c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724452"
---
# <a name="iactivescriptprofilercontrol3-interface"></a>IActiveScriptProfilerControl3 インターフェイス
スクリプト エンジンに関連付けられた GC ヒープ オブジェクトを列挙するメソッドを提供します。  
  
## <a name="syntax"></a>構文  
  
```  
interface IActiveScriptProfilerControl3 : IActiveScriptProfilerControl2  
```  
  
## <a name="methods"></a>メソッド  
 [IActiveScriptProfilerControl3::EnumHeap メソッド](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)  
 インターフェイスを返します ([IActiveScriptProfilerHeapEnum インターフェイス](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)) を使用して、関連付けられているスクリプト エンジンのコンテキストで GC ヒープのオブジェクトを反復処理をすることができます。