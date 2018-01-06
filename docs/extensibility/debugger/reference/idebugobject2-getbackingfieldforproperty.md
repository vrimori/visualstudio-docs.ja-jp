---
title: "IDebugObject2::GetBackingFieldForProperty |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords: IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f8833e3d2b686e1c350e1094aaa9bdfe925586a7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="see-also"></a>参照  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)