---
title: IActiveScriptError::GetSourcePosition |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptError.GetSourcePosition
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptError_GetSourcePosition
ms.assetid: ae9b26b1-82a7-4645-9686-3261d8248664
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d63310a8ba5cfda39d48a482eaf7c345cd492adc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645842"
---
# <a name="iactivescripterrorgetsourceposition"></a>IActiveScriptError::GetSourcePosition
スクリプト エンジンでスクリプトの実行中にエラーが発生したソース コード内の位置を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetSourcePosition(  
    DWORD *pdwSourceContext,  // context cookie  
    ULONG *pulLineNumber,     // line number of error  
    LONG *pichCharPosition    // character position of error  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pdwSourceContext`  
 [out]コンテキストを識別する cookie を受け取る変数のアドレスです。 このパラメーターの解釈は、ホスト アプリケーションによって異なります。  
  
 `pulLineNumber`  
 [out]エラーが発生したソース ファイル内の行番号を受け取る変数のアドレスです。  
  
 `pichCharPosition`  
 [out]エラーが発生した行の文字位置を受け取る変数のアドレス。  
  
## <a name="return-value"></a>戻り値  
 返します`S_OK`成功した場合、または`E_FAIL`場合は、場所を取得できませんでした。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)