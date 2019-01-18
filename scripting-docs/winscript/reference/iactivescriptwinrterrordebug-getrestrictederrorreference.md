---
title: IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference
ms.assetid: fcf60971-9518-4b24-a3a6-1e2e30a02cea
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f801171848537a564ec30e2677a716e6ee7f6cc9
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344136"
---
# <a name="iactivescriptwinrterrordebuggetrestrictederrorreference"></a>IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference
返します、Windows ランタイムでは、使用可能な場合、参照のエラーが制限されています。  
  
> [!IMPORTANT]
>  [IActiveScriptWinRTErrorDebug インターフェイス](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)PDM v11.0 以降によって実装された以降には。 activdbg100.h にあります。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetRestrictedErrorReference([out] BSTR * referenceString);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `referenceString`  
 [out]参照エラーの文字列。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptWinRTErrorDebug インターフェイス](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)