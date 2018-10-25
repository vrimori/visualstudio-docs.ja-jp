---
title: IDebugMethodField::GetGlobalContainer |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugMethodField::GetGlobalContainer
helpviewer_keywords:
- IDebugMethodField::GetGlobalContainer method
ms.assetid: 041ac5aa-0b80-4310-b9ae-b88f8e7e0e5f
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8349c4fd02d771adacb49d3eb4b310ae3ef4741c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892508"
---
# <a name="idebugmethodfieldgetglobalcontainer"></a>IDebugMethodField::GetGlobalContainer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

メソッドのグローバル コンテナーを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 [out]返します、 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)このメソッドが定義されているモジュールを表します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 返された[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)オブジェクトは、モジュール全体を表しており、人為的なオブジェクトは、つまり、モジュール自体には、実際のクラスはありませんで表すことができます、`IDebugClassField`さまざまなことにより、オブジェクト列挙され、検出されたモジュールの要素です。  
  
## <a name="see-also"></a>関連項目  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)

