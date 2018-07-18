---
title: IDebugBinder::Bind |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder::Bind
helpviewer_keywords:
- IDebugBinder::Bind method
ms.assetid: 15a11ad7-0fcc-4e80-ae34-8a7dd7bae3c3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c49e4254df9ec06813499237054ec916bb4b6c1b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100066"
---
# <a name="idebugbinderbind"></a>IDebugBinder::Bind
このメソッドは、メモリ コンテキストまたはシンボルの現在の値を格納しているオブジェクトを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Bind(   
   IDebugObject*  pContainer,  
   IDebugField*   pField,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int Bind(  
   IDebugObject     pContainer,  
   IDebugField      pField,  
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pContainer`  
 [in][IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)によって参照されている子を格納している`pField`です。  
  
 `pField`  
 [in][IDebugField](../../../extensibility/debugger/reference/idebugfield.md)を表す記号です。  
  
 `ppObject`  
 [out]返します、`IDebugObject`記号のインスタンスを表すです。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)