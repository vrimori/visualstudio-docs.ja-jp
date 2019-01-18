---
title: IDebugApplication::FIsAutoJitDebugEnabled |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.FIsAutoJitDebugEnabled
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::FIsAutoJitDebugEnabled
ms.assetid: 0551dd3b-e6eb-442a-8201-418f96fe62df
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b06d223d76ed741eef6b379ace6b522248ded2e1
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348218"
---
# <a name="idebugapplicationfisautojitdebugenabled"></a>IDebugApplication::FIsAutoJitDebugEnabled
ジャストイン タイム (JIT) デバッガーが自動デバッグ ダム ホストに登録されているかどうかを決定します。  
  
## <a name="syntax"></a>構文  
  
```cpp
BOOL FIsAutoJitDebugEnabled();  
```  
  
#### <a name="parameters"></a>パラメーター  
 このメソッドには、パラメーターはありません。  
  
## <a name="return-value"></a>戻り値  
 メソッドが返すかどうかは、メソッドが成功し、JIT デバッガーが自動デバッグ ダム ホストに登録されている、`TRUE`します。 返しますそれ以外の場合、`FALSE`します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、JIT デバッガーが自動デバッグ ダム ホストに登録されている場合を決定します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugApplication インターフェイス](../../winscript/reference/idebugapplication-interface.md)