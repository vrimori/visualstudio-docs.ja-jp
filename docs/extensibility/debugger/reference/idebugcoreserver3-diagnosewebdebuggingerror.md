---
title: "IDebugCoreServer3::DiagnoseWebDebuggingError |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 04a8ecbb1bfdc7f14f6b493df7f1dc9e16b53cd6
ms.lasthandoff: 02/22/2017

---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
理由、auto-attach を特定する試みが失敗しました。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT DiagnoseWebDebuggingError(  
   LPCWSTR pszUrl  
);  
```  
  
```c#  
int DiagnoseWebDebuggingError(  
   string pszUrl  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pszUrl`  
 [in]現在使用されていません。null 値を常に設定する必要があります。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返す`S_OK`。 そうしないと、エラー コードを返します。 その他の一般的なリターン コードを次に示します。  
  
|コード|説明|  
|----------|-----------------|  
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|リモート サーバーのデバッグの開始が失敗した理由を判断できません。|  
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|おそらくアクセス許可が不十分のためのリモート サーバーではデバッグできません、DEBUG の動詞が有効になっていませんか。|  
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|Web サーバーでは、ロックダウンされているし、デバッグを有効にする必要がある DEBUG の動詞をブロックしています。|  
  
## <a name="see-also"></a>関連項目  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
