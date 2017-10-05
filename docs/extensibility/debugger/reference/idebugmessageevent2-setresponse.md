---
title: "IDebugMessageEvent2::SetResponse |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMessageEvent2::SetResponse
helpviewer_keywords:
- IDebugMessageEvent2::SetResponse method
- SetResponse method
ms.assetid: 2a5e318d-3225-4abd-83f1-28323baff6c0
caps.latest.revision: 10
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
ms.openlocfilehash: f8b1883ab4c71d066fcdb816bc98ae9bdbb0831b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

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
 [in]Win32 の規則を使用して、応答を指定`MessageBox`関数。 参照してください、 [AfxMessageBox](http://msdn.microsoft.com/Library/d66d0328-cdcc-48f6-96a4-badf089099c8)詳細関数。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [AfxMessageBox](http://msdn.microsoft.com/Library/d66d0328-cdcc-48f6-96a4-badf089099c8)
