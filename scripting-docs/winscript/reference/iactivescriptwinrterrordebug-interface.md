---
title: IActiveScriptWinRTErrorDebug インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptWinRTErrorDebug Interface
ms.assetid: 58b45096-633f-479f-95c4-8eae7376d3a1
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2355b9aa38abbed2ca66964a07bb47082eb76c32
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346502"
---
# <a name="iactivescriptwinrterrordebug-interface"></a>IActiveScriptWinRTErrorDebug インターフェイス
拡張の Windows ランタイム エラー情報を提供する JavaScript エンジンによって実装される、 [BREAKREASON 列挙型](../../winscript/reference/breakreason-enumeration.md)イベント。 取得する QueryInterface を行うことができます、 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)オブジェクト。  
  
> [!IMPORTANT]
>  このインターフェイスは、PDM v11.0 以降によって実装されます。 activdbg100.h にあります。  
  
## <a name="methods"></a>メソッド  
 `IActiveScriptWinRTErrorDebug` インターフェイスは、以下のメソッドを公開します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IActiveScriptWinRTErrorDebug::GetCapabilitySid](../../winscript/reference/iactivescriptwinrterrordebug-getcapabilitysid.md)|使用可能な場合は、Windows ランタイム エラーでは、機能の SID を返します。|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorreference.md)|返します、Windows ランタイムには、使用可能な場合のエラーの参照の文字列が制限されています。|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorString](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorstring.md)|返します、Windows ランタイムでは、使用可能な場合、エラーの文字列が制限されています。|