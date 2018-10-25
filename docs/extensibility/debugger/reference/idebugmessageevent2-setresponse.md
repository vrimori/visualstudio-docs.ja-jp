---
title: IDebugMessageEvent2::SetResponse |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMessageEvent2::SetResponse
helpviewer_keywords:
- IDebugMessageEvent2::SetResponse method
- SetResponse method
ms.assetid: 2a5e318d-3225-4abd-83f1-28323baff6c0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 73c5b29293b8e06ec79195621c8744c71a8bdd58
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49936148"
---
# <a name="idebugmessageevent2setresponse"></a>IDebugMessageEvent2::SetResponse
メッセージ ボックスから存在する場合、応答を設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetResponse(   
   DWORD dwResponse  
);  
```  
  
```csharp  
int SetResponse(   
   uint dwResponse  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwResponse`  
 [in]Win32 の規則を使用して、応答を指定します`MessageBox`関数。 参照してください、 [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)詳細については、関数。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)