---
title: IDebugObject2::IsEncOutdated |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject2::IsEncOutdated
helpviewer_keywords:
- IDebugObject2::IsEncOutdated method
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ab51e2dbc75de33bcafe28295b5e47e4b4358538
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122523"
---
# <a name="idebugobject2isencoutdated"></a>IDebugObject2::IsEncOutdated
このメソッドは、またはこのオブジェクトの親コンテナーのエディット コンティニュの状態が最新かどうかを判断します。 カスタム式エバリュエーターではこのメソッドを常に返すを実装していません`E_NOTIMPL`です。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT IsEncOutdated(  
   BOOL* pfEncOutdated  
);  
```  
  
```csharp  
int IsEncOutdated(  
   out int pfEncOutdated  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pfEncOutdated`  
 [out]0 以外 (`TRUE`) 場合は、エディット コンティニュの状態は最新では、0 (`FALSE`) されていない場合。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
> [!NOTE]
>  カスタム式エバリュエーターを常に返します`E_NOTIMPL`です。  
  
## <a name="see-also"></a>関連項目  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)