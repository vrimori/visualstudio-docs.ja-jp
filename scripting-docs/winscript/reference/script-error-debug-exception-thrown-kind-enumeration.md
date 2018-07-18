---
title: SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND 列挙型 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: b3aa4966-e110-4b30-b368-1281a9740dbd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6fe5b308ea75956d9e5826b4daadaef3a823141f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734152"
---
# <a name="scripterrordebugexceptionthrownkind-enumeration"></a>SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND 列挙型
スローされた例外の種類を示します。 この列挙体を使って、 [IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md)メソッドです。  
  
> [!IMPORTANT]
>  これらの定数は、PDM Version 11.0 以降によって実装されます。 activdbg100.h にあります。  
  
## <a name="syntax"></a>構文  
  
```  
typedef SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|値|説明|  
|------------|-----------|-----------------|  
|ETK_FIRST_CHANCE|0x00000000|例外は初回例外です。|  
|ETK_USER_UNHANDLED|0x00000001|例外は、ユーザー コードでハンドルされません。|  
|ETK_UNHANDLED|0x00000002|例外は、コードでハンドルされません。|  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptErrorDebug110 インターフェイス](../../winscript/reference/iactivescripterrordebug110-interface.md)