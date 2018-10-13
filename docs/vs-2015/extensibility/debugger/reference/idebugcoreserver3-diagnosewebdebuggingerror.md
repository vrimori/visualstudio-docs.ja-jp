---
title: IDebugCoreServer3::DiagnoseWebDebuggingError |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7ec9f0ae560d28304c3d739011e4d6eb509d66d0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49176684"
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Auto-attach できなかった理由を特定する試行が失敗しました。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 [in]使用されていません。null 値に常に設定する必要があります。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。 次に、その他の一般的なリターン コードを示します。  
  
|コード|説明|  
|----------|-----------------|  
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|デバッグを開始するリモート サーバーが失敗した理由を判断できません。|  
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|十分なアクセス許可の可能性があるため、リモート サーバーでデバッグすることはできません、DEBUG の動詞が有効になっていませんか。|  
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|Web サーバーがロックダウンされているし、デバッグを有効にするには、必要な DEBUG 動詞をブロックします。|  
  
## <a name="see-also"></a>関連項目  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)

