---
title: IJsDebugProcess インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a7ad5525-55b7-4c68-a4f7-c508f7877712
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ecdec77a8bcb3c1fb8a1dc64c63b363b4f001fde
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086659"
---
# <a name="ijsdebugprocess-interface"></a>IJsDebugProcess インターフェイス
ターゲット プロセスを検査および制御するためのルーチンを提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp
IJsDebugProcess : public IUnknown;  
```  
  
## <a name="members"></a>メンバー  
  
### <a name="public-methods"></a>パブリック メソッド  
  
|名前|説明|  
|----------|-----------------|  
|[IJsDebugProcess::CreateBreakPoint メソッド](../../winscript/reference/ijsdebugprocess-createbreakpoint-method.md)|指定されたドキュメントの位置にブレークポイントを設定します。|  
|[IJsDebugProcess::CreateStackWalker メソッド](../../winscript/reference/ijsdebugprocess-createstackwalker-method.md)|スタック ウォーカーのファクトリ メソッド。|  
|[IJsDebugProcess::PerformAsyncBreak メソッド](../../winscript/reference/ijsdebugprocess-performasyncbreak-method.md)|スクリプト エンジンを中断モードにして、次のスクリプト命令で中断させます。|  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** jscript9diag.h です  
  
## <a name="see-also"></a>関連項目  
 [Windows スクリプト インターフェイスのリファレンス](../../winscript/reference/windows-script-interfaces-reference.md)