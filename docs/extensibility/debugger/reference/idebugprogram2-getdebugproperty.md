---
title: IDebugProgram2::GetDebugProperty |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 49c83cb4ca1dccbdf1e28d545bdcaa711e3241a6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122003"
---
# <a name="idebugprogram2getdebugproperty"></a>IDebugProgram2::GetDebugProperty
プログラムのプロパティを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetDebugProperty(   
   IDebugProperty2** ppProperty  
);  
```  
  
```csharp  
int GetDebugProperty(   
   out IDebugProperty2 ppProperty  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppProperty`  
 [out]返します、 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)プログラムのプロパティを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 このメソッドによって返されるプロパティは、プログラムに固有です。 プログラムは、1 つ以上のプロパティを返す必要がある場合、 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)このメソッドによって返されるオブジェクトは、追加のプロパティと呼び出し元のコンテナー、 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)メソッドを返します、。すべてのプロパティの一覧です。  
  
 プログラムが公開される任意の数と種類の追加のプロパティを使用して記述できる`IDebugProperty2`インターフェイスです。 IDE には、汎用プロパティ ブラウザーのユーザー インターフェイスでプロパティを追加したプログラムが表示されます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)