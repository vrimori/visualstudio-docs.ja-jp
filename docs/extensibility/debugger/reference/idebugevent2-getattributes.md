---
title: IDebugEvent2::GetAttributes |Microsoft Docs
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
ms.openlocfilehash: 515775a064d1e260d9eb028c6e1b6020b7d642cd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49935303"
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
 [out]フラグの組み合わせ、[複数](../../../extensibility/debugger/reference/eventattributes.md)列挙体。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)インターフェイスはすべてのイベントに共通です。 このメソッドは、イベントの種類を説明します。たとえば、同期または非同期のイベントし、停止イベントです。  
  
## <a name="see-also"></a>関連項目  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)