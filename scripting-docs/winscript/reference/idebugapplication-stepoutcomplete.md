---
title: IDebugApplication::StepOutComplete |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.StepOutComplete
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::StepOutComplete
ms.assetid: 9675b214-7be5-4cf7-a63f-7865f3c54371
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c344f0316bda6ed5ef895c1b88ae7b1a6465e73
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725642"
---
# <a name="idebugapplicationstepoutcomplete"></a>IDebugApplication::StepOutComplete
シングル ステップ モードで言語エンジンを呼び出し元に、プロセスのデバッグ マネージャーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT StepOutComplete();  
```  
  
#### <a name="parameters"></a>パラメーター  
 このメソッドには、パラメーターはありません。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 言語エンジンでは、その呼び出し元に返される直前に、シングル ステップ モードでこのメソッドを呼び出します。 プロセスのデバッグ マネージャーでは、最初のチャンスに中断する必要があります、他のすべてのスクリプト エンジンに通知するのにこの営業案件を使用します。 この手法は、モードの実装方法、言語間の手順です。  
  
## <a name="see-also"></a>関連項目  
 [IDebugApplication インターフェイス](../../winscript/reference/idebugapplication-interface.md)