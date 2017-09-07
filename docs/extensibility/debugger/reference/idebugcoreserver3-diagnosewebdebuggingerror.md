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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 2c9ed64c1db1472e334333f3c2cb6d1bfb017c25
ms.contentlocale: ja-jp
ms.lasthandoff: 09/06/2017

---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
Auto-attach 理由を特定する試みが失敗しました。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DiagnoseWebDebuggingError(  
   LPCWSTR pszUrl  
);  
```  
  
```csharp  
int DiagnoseWebDebuggingError(  
   string pszUrl  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pszUrl`  
 [in]現在使用されていません。null 値に設定する必要があります。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。 その他の一般的なリターン コードを次に示します。  
  
|コード|説明|  
|----------|-----------------|  
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|リモート サーバーがデバッグの開始に失敗した原因を特定できません。|  
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|アクセス許可が不十分などによって、リモート サーバー上でデバッグできませんか、DEBUG の動詞が有効になっていないためです。|  
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|Web サーバーでは、ロックダウンされているし、デバッグを有効にする必要がある DEBUG の動詞がブロックしています。|  
  
## <a name="see-also"></a>関連項目  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
