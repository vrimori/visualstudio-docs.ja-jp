---
title: IJsDebugStackWalker インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 3fe30394-49c8-48e9-bde9-ffe5d79b2121
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d79950c6d5595a0a8a95623a7510c5523f16e41b
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087900"
---
# <a name="ijsdebugstackwalker-interface"></a>IJsDebugStackWalker インターフェイス
指定したスレッドのスタック ウォーカーを表します。  
  
## <a name="syntax"></a>構文  
  
```cpp
IJsDebugStackWalker : public IUnknown;  
```  
  
## <a name="members"></a>メンバー  
  
### <a name="public-methods"></a>パブリック メソッド  
  
|名前|説明|  
|----------|-----------------|  
|[IJsDebugStackWalker::GetNext メソッド](../../winscript/reference/ijsdebugstackwalker-getnext-method.md)|次のフレームを取得します。|  
  
## <a name="remarks"></a>Remarks  
 スタック ウォーカーはターゲット プロセスの停止中にのみ作成でき、そのプロセスが再び続行されると無効になります。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** jscript9diag.h です  
  
## <a name="see-also"></a>関連項目  
 [Windows スクリプト インターフェイスのリファレンス](../../winscript/reference/windows-script-interfaces-reference.md)