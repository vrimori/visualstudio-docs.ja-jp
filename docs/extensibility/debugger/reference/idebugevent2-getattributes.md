---
title: IDebugEvent2::GetAttributes |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEvent2::GetAttributes
helpviewer_keywords:
- IDebugEvent2::GetAttributes
ms.assetid: 2ac5b5fb-da17-43f7-811a-313f677e60d7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6d6305d7000456eb81cf01c9e85e6c2a421ed800
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugevent2getattributes"></a>IDebugEvent2::GetAttributes
このデバッグ イベントの属性を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetAttribute(   
   DWORD* pdwAttrib  
);  
```  
  
```csharp  
int GetAttribute(   
   out uint pdwAttrib  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pdwAttrib`  
 [out]フラグの組み合わせ、[複数](../../../extensibility/debugger/reference/eventattributes.md)列挙します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)インターフェイスは、すべてのイベントに共通します。 このメソッドは、イベントの種類を示しますたとえばが同期または非同期のイベントおよび停止イベントをします。  
  
## <a name="see-also"></a>関連項目  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)