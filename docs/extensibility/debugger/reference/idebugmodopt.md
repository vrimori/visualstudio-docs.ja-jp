---
title: IDebugModOpt |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugModOpt interface
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0477f8b3a39bd919a814828377228c5ccc02bd11
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugmodopt"></a>IDebugModOpt
デバッグ オプションの修飾子を表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugModOpt : IUnknown  
```  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 取得した、 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)クラスまたはメソッドを表すオブジェクト。  
  
## <a name="methods"></a>メソッド  
 このインターフェイスでは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetModOpts](../../../extensibility/debugger/reference/idebugmodopt-getmodopts.md)|省略可能な修飾子の一覧を取得します。|  
  
## <a name="requirements"></a>要件  
 ヘッダー: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll