---
title: IDebugStackFrame インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrame interface
ms.assetid: e95c1b4f-17c1-490c-a56b-c25fa45d4822
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0834abbedf88b911dd952c1f3928c5da3414abec
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348543"
---
# <a name="idebugstackframe-interface"></a>IDebugStackFrame インターフェイス
スレッド スタック上の論理スタック フレームを表します。 呼び出す、`IDebugStackFrame::QueryInterface`メソッドを取得する、`IDebugExpressionContext`インターフェイスで、式の評価とウォッチ ウィンドウを使用します。  
  
 継承されたメソッドだけでなく`IUnknown`、`IDebugStackFrame`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugStackFrame::GetCodeContext](../../winscript/reference/idebugstackframe-getcodecontext.md)|スタック フレームに関連付けられている現在のコード コンテキストを返します。|  
|[IDebugStackFrame::GetDescriptionString](../../winscript/reference/idebugstackframe-getdescriptionstring.md)|スタック フレームの短い、または時間の長いテキストの説明を返します。|  
|[IDebugStackFrame::GetLanguageString](../../winscript/reference/idebugstackframe-getlanguagestring.md)|言語の短い、または時間の長いテキストの説明を返します。|  
|[IDebugStackFrame::GetThread](../../winscript/reference/idebugstackframe-getthread.md)|このスタック フレームに関連付けられているスレッドを返します。|  
|[IDebugStackFrame::GetDebugProperty](../../winscript/reference/idebugstackframe-getdebugproperty.md)|現在のフレームのプロパティ ブラウザーを返します。|