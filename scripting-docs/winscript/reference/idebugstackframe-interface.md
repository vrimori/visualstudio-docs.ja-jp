---
title: "IDebugStackFrame インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugStackFrame interface
ms.assetid: e95c1b4f-17c1-490c-a56b-c25fa45d4822
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 36fa0ba2d1b4049ad41ff0502ed33be0a706d9f6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframe-interface"></a>IDebugStackFrame インターフェイス
スレッドのスタック上で論理スタック フレームを表します。 呼び出す、`IDebugStackFrame::QueryInterface`を取得するメソッド、`IDebugExpressionContext`インターフェイスで、式の評価およびウォッチ ウィンドウを許可します。  
  
 継承されたメソッドだけでなく`IUnknown`、`IDebugStackFrame`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugStackFrame::GetCodeContext](../../winscript/reference/idebugstackframe-getcodecontext.md)|スタック フレームに関連付けられている現在のコードのコンテキストを返します。|  
|[IDebugStackFrame::GetDescriptionString](../../winscript/reference/idebugstackframe-getdescriptionstring.md)|スタック フレームの短い、または長いテキストの説明を返します。|  
|[IDebugStackFrame::GetLanguageString](../../winscript/reference/idebugstackframe-getlanguagestring.md)|言語の短い、または長いテキストの説明を返します。|  
|[IDebugStackFrame::GetThread](../../winscript/reference/idebugstackframe-getthread.md)|このスタック フレームに関連付けられているスレッドを返します。|  
|[IDebugStackFrame::GetDebugProperty](../../winscript/reference/idebugstackframe-getdebugproperty.md)|現在のフレームのプロパティ ブラウザーを返します。|