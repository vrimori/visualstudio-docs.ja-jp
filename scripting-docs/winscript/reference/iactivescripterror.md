---
title: IActiveScriptError |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptError interface
ms.assetid: c8e0288d-38ff-4145-a7e3-f8cdfb72eefe
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 540a4a338ae8ebfcacae66b1890075c20bdee086
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347100"
---
# <a name="iactivescripterror"></a>IActiveScriptError
このインターフェイスを実装するオブジェクトが渡される、 [IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)メソッド スクリプト エンジンがハンドルされないエラーを検出するたびにします。 ホストは、発生したエラーに関する情報を取得するには、このオブジェクトのメソッドを呼び出します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IActiveScriptError::GetExceptionInfo](../../winscript/reference/iactivescripterror-getexceptioninfo.md)|エラーに関する情報を取得します。|  
|[IActiveScriptError::GetSourcePosition](../../winscript/reference/iactivescripterror-getsourceposition.md)|エラーが発生したソース コード内の場所を取得します。|  
|[IActiveScriptError::GetSourceLineText](../../winscript/reference/iactivescripterror-getsourcelinetext.md)|エラーが発生したソース ファイル内の行を取得します。|  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト インターフェイス](../../winscript/reference/active-script-interfaces.md)