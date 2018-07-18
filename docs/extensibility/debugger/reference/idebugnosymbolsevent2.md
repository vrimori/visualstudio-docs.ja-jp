---
title: IDebugNoSymbolsEvent2 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bb7719ff66ac284d07da2ddfca25fe6898c93220
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31112409"
---
# <a name="idebugnosymbolsevent2"></a>IDebugNoSymbolsEvent2
信号、[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]デバッガーの UI をシンボルことができない、起動した実行可能ファイルのあるユーザーに警告します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugNoSymbolsEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジンによって実装され、によって消費されている、[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]デバッガーの UI。  
  
## <a name="requirements"></a>要件  
 ヘッダー: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll