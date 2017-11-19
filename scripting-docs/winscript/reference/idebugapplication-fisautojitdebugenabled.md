---
title: "IDebugApplication::FIsAutoJitDebugEnabled |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.FIsAutoJitDebugEnabled
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::FIsAutoJitDebugEnabled
ms.assetid: 0551dd3b-e6eb-442a-8201-418f96fe62df
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 268a10cc829e2d217bb9a90b355405dd8f3b15b6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationfisautojitdebugenabled"></a>IDebugApplication::FIsAutoJitDebugEnabled
・ イン タイム (JIT) のデバッガーが自動デバッグ ダム ホストに登録されているかどうかを判断します。  
  
## <a name="syntax"></a>構文  
  
```  
BOOL FIsAutoJitDebugEnabled();  
```  
  
#### <a name="parameters"></a>パラメーター  
 このメソッドには、パラメーターはありません。  
  
## <a name="return-value"></a>戻り値  
 メソッドが返すかどうかは、メソッドが成功し、JIT デバッガーが自動デバッグ ダム ホストに登録されている、`TRUE`です。 返しますそれ以外の場合、`FALSE`です。  
  
## <a name="remarks"></a>コメント  
 このメソッドは、JIT デバッガーが自動デバッグ ダム ホストに登録されている場合を判断します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugApplication インターフェイス](../../winscript/reference/idebugapplication-interface.md)