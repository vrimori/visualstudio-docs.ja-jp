---
title: IDebugModOpt |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugModOpt interface
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 65b02ed1a3270c74430122245f83e47bc31bdbff
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49302426"
---
# <a name="idebugmodopt"></a>IDebugModOpt
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

デバッグ オプションの修飾子を表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugModOpt : IUnknown  
```  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 取得した、 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)クラスまたはメソッドを表すオブジェクト。  
  
## <a name="methods"></a>メソッド  
 このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetModOpts](../../../extensibility/debugger/reference/idebugmodopt-getmodopts.md)|オプションの修飾子の一覧を取得します。|  
  
## <a name="requirements"></a>要件  
 ヘッダー: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll

