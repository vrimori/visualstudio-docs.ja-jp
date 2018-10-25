---
title: IDebugObject2::GetBackingFieldForProperty |Microsoft Docs
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
ms.openlocfilehash: 9d788d048fc428825cbc667b18424b32c68ddc5c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49840234"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
フィールドまたは変数を取得します (ある場合) をこのオブジェクトによって表されるプロパティをサポートする場合があります。  
  
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
  
## <a name="remarks"></a>Remarks  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)マネージ コード クラスのプロパティ、つまり、get メソッドを表すオブジェクト、または set アクセサー。 このようなプロパティには、一般にケェルェニェホォウーォノェマ ｡ ｢ プロパティ値を格納する変数が必要です。 この変数は、バッキング フィールドと呼ばれます。 オブジェクトのバッキング フィールドがない場合は、確認して null 値を返す: いくつかの呼び出し元は、戻り値に注意を支払う必要はありませんで null 値が返されたかどうかに表示する代わりになります`ppObject`します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)