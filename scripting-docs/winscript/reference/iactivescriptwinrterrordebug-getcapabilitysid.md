---
title: IActiveScriptWinRTErrorDebug::GetCapabilitySid |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptWinRTErrorDebug::GetCapabilitySid
ms.assetid: 469463d2-5e73-4c53-9ffd-d0ca7460aa5c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2e0e9f642e780b745f8b66734893345618a43460
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349825"
---
# <a name="iactivescriptwinrterrordebuggetcapabilitysid"></a>IActiveScriptWinRTErrorDebug::GetCapabilitySid
使用可能な場合は、Windows ランタイム エラーでは、機能の SID を返します。  
  
> [!IMPORTANT]
>  [IActiveScriptWinRTErrorDebug インターフェイス](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)PDM v11.0 以降によって実装された以降には。 activdbg100.h にあります。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetCapabilitySid([out] BSTR * capabilitySid);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `capabilitySid`  
 エラーの SID の機能です。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptWinRTErrorDebug インターフェイス](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)