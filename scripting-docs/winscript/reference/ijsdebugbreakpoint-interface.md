---
title: IJsDebugBreakPoint インターフェイス |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 791c8488-21e7-46be-b1b4-fe74117cf200
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6ed749953aeffbadb450b2a21ef86ffb619eb6a6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728322"
---
# <a name="ijsdebugbreakpoint-interface"></a>IJsDebugBreakPoint インターフェイス
ブレークポイントを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IJsDebugBreakPoint : public IUnknown;  
```  
  
## <a name="members"></a>メンバー  
  
### <a name="public-methods"></a>パブリック メソッド  
  
|名前|説明|  
|----------|-----------------|  
|[IJsDebugBreakPoint::Delete メソッド](../../winscript/reference/ijsdebugbreakpoint-delete-method.md)|ブレークポイントを削除します。|  
|[IJsDebugBreakPoint::Disable メソッド](../../winscript/reference/ijsdebugbreakpoint-disable-method.md)|ブレークポイントを無効にします。|  
|[IJsDebugBreakPoint::Enable メソッド](../../winscript/reference/ijsdebugbreakpoint-enable-method.md)|ブレークポイントを有効にします。|  
|[IJsDebugBreakPoint::GetDocumentPosition メソッド](../../winscript/reference/ijsdebugbreakpoint-getdocumentposition-method.md)|ブレークポイントが関連付けられたステートメントの位置を返します。|  
|[IJsDebugBreakPoint::IsEnabled メソッド](../../winscript/reference/ijsdebugbreakpoint-isenabled-method.md)|ブレークポイントが有効かどうかを指定します。|  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jscript9diag.h です  
  
## <a name="see-also"></a>関連項目  
 [Windows スクリプト インターフェイスのリファレンス](../../winscript/reference/windows-script-interfaces-reference.md)