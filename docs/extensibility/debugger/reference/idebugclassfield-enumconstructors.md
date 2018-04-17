---
title: IDebugClassField::EnumConstructors |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugClassField::EnumConstructors
helpviewer_keywords:
- IDebugClassField::EnumConstructors method
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: aa525f50a0ffd18f136cfa23ae05a8e2ba193d0d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugclassfieldenumconstructors"></a>IDebugClassField::EnumConstructors
このクラスのコンス トラクターの列挙子を作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumConstructors(   
   CONSTRUCTOR_ENUM   cMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumConstructors(  
   CONSTRUCTOR_ENUM     cMatch,   
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `cMatch`  
 [in]値、 [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)列挙型にコンス トラクターの型を指定する列挙です。  
  
 `ppEnum`  
 [out]返します、 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)コンス トラクターの一覧を表すオブジェクト。 コンス トラクターが存在しない場合は、null 値を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。 または、コンス トラクターが存在しない場合は S_FALSE を返します。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 列挙体の各要素は、 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)コンス トラクター メソッドを記述するオブジェクト。  
  
 通常、コンス トラクターの一覧では、コンパイラによって提供される既定のコンス トラクターは含まれません。  
  
## <a name="see-also"></a>関連項目  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)