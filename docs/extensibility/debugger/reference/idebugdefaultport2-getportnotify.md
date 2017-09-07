---
title: "IDebugDefaultPort2::GetPortNotify |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
caps.latest.revision: 11
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
ms.openlocfilehash: 11a0f157ff10fb7f22d7571b22ab0263c430e5dd
ms.contentlocale: ja-jp
ms.lasthandoff: 09/06/2017

---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
このメソッドは、取得、 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)このポートのインターフェイスです。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetPortNotify(  
   IDebugPortNotify2** ppPortNotify  
);  
```  
  
```csharp  
int GetPortNotify(  
   out IDebugPortNotify2 ppPortNotify  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppPortNotify`  
 [out][IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 通常、`QueryInterface`メソッドが実装するオブジェクト、 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)インターフェイスを取得する、 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)インターフェイスです。 ただし、別のオブジェクトに必要なインターフェイスを実装する場合があります。 このメソッドは、このような状況を非表示にし、返します、`IDebugPortNotify2`最も適切なオブジェクトからのインターフェイスです。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)
