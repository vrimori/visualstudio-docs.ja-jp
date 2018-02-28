---
title: "IDebugProgram2::GetDebugProperty |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2263b96f64a72e9c89061d1ca3b7792526a8231b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="see-also"></a>参照  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)