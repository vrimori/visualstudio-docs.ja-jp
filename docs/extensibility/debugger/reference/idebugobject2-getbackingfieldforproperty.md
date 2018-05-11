---
title: IDebugObject2::GetBackingFieldForProperty |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7729f55c93274796d3c81f280618653b873bc40b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
(存在する場合)、フィールドまたは変数を取得するオブジェクトによって表されるプロパティがバッキング可能性があります。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetBackingFieldForProperty(  
   IDebugObject2** ppObject  
);  
```  
  
```csharp  
int GetBackingFieldForProperty(  
   out IDebugObject2 ppObject  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppObject`  
 [out][IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)バッキング フィールドを記述するオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)マネージ コード クラスのプロパティ、つまり、get メソッドを表すオブジェクトやアクセサーを設定します。 このようなプロパティには、プロパティによって操作の値を変数通常必要があります。 この変数は、バッキング フィールドと呼ばれます。 オブジェクトのバッキング フィールドがない場合は、し確認を null 値を返す: いくつかの呼び出し元は、戻り値に注意を払っていない可能性がありますで null 値が返されたかどうかに表示する代わりになります`ppObject`です。  
  
## <a name="see-also"></a>関連項目  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)