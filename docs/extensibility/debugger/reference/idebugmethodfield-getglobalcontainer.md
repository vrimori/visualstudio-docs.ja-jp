---
title: "IDebugMethodField::GetGlobalContainer |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMethodField::GetGlobalContainer
helpviewer_keywords:
- IDebugMethodField::GetGlobalContainer method
ms.assetid: 041ac5aa-0b80-4310-b9ae-b88f8e7e0e5f
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: b2fef7bf82992b6fdaaadbbd2bee6a9e36f68ad0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmethodfieldgetglobalcontainer"></a>IDebugMethodField::GetGlobalContainer
メソッドのグローバルのコンテナーを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetGlobalContainer(  
   IDebugClassField** ppClass  
);  
```  
  
```csharp  
int GetGlobalContainer(  
   out IDebugClassField ppClass  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppClass`  
 [out]返します、 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)このメソッドが定義されているモジュールを表すです。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 返された[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)オブジェクトはモジュール全体を表し、人為的なオブジェクトしますつまり、モジュール自体には、実際のクラスはありませんがで表すことができます、`IDebugClassField`さまざまなをすることにより、オブジェクト。列挙され、検出するモジュールの要素です。  
  
## <a name="see-also"></a>参照  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)