---
title: "IDebugIDECallback::DisplayMessage |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugIDECallback::DisplayMessage
ms.assetid: c19b48ee-b370-4fce-91fe-f82bf1e63179
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
ms.openlocfilehash: 7b3f7e5fde160bc9d1e5ece61b810090c5dd7d9b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="idebugidecallbackdisplaymessage"></a>IDebugIDECallback::DisplayMessage
指定したメッセージ文字列をデバッガーの出力ウィンドウに送信します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DisplayMessage (  
   LPCOLESTR szMessage  
);  
```  
  
```csharp  
int DisplayMessage (  
   string szMessage  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `szMessage`  
 [in]デバッガーの出力ウィンドウに表示するメッセージ文字列。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)
