---
title: IRemoteDebugApplication::ResumeFromBreakPoint |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.ResumeFromBreakPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::ResumeFromBreakPoint
ms.assetid: a613cc2b-1d69-4713-a235-64372c253b4a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0603ef19426e27324daa39bf769e2c0667477be3
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089077"
---
# <a name="iremotedebugapplicationresumefrombreakpoint"></a>IRemoteDebugApplication::ResumeFromBreakPoint
ブレークポイントになっているアプリケーションを継続します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT ResumeFromBreakPoint(  
   IRemoteDebugApplicationThread*  prptFocus,  
   BREAKRESUMEACTION               bra,  
   ERRORRESUMEACTION               era  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `prptFocus`  
 [in]モードでは、ステップ実行モードの影響を受けるには、スレッドをステップ実行します。  
  
 `bra`  
 [in]アプリケーションの再開時に実行するアクション。  
  
 `era`  
 [in]エラーのため、アプリケーションが停止している場合は、実行するアクション。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、ブレークポイントになっているアプリケーションを続行します。  
  
## <a name="see-also"></a>関連項目  
 [IRemoteDebugApplication インターフェイス](../../winscript/reference/iremotedebugapplication-interface.md)   
 [BREAKRESUMEACTION 列挙型](../../winscript/reference/breakresumeaction-enumeration.md)   
 [ERRORRESUMEACTION 列挙型](../../winscript/reference/errorresumeaction-enumeration.md)