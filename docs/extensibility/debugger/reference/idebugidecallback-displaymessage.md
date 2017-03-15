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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d3aa786eb2440112713883ed6c600fc845975127
ms.lasthandoff: 02/22/2017

---
# <a name="idebugidecallbackdisplaymessage"></a>IDebugIDECallback::DisplayMessage
デバッガーの出力ウィンドウには、指定したメッセージ文字列を送信します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT DisplayMessage (  
   LPCOLESTR szMessage  
);  
```  
  
```c#  
int DisplayMessage (  
   string szMessage  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `szMessage`  
 [in]デバッガーの出力ウィンドウに表示するメッセージ文字列。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返す`S_OK`。 そうしないと、エラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)
