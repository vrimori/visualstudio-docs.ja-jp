---
title: "IJsDebugStackWalker インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3fe30394-49c8-48e9-bde9-ffe5d79b2121
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dbea11bf1188d148818ea8a082bceec76c704c2b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugstackwalker-interface"></a>IJsDebugStackWalker インターフェイス
指定したスレッドのスタック ウォーカーを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IJsDebugStackWalker : public IUnknown;  
```  
  
## <a name="members"></a>メンバー  
  
### <a name="public-methods"></a>パブリック メソッド  
  
|名前|説明|  
|----------|-----------------|  
|[IJsDebugStackWalker::GetNext メソッド](../../winscript/reference/ijsdebugstackwalker-getnext-method.md)|次のフレームを取得します。|  
  
## <a name="remarks"></a>コメント  
 スタック ウォーカーはターゲット プロセスの停止中にのみ作成でき、そのプロセスが再び続行されると無効になります。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jscript9diag.h です  
  
## <a name="see-also"></a>関連項目  
 [Windows スクリプト インターフェイスのリファレンス](../../winscript/reference/windows-script-interfaces-reference.md)