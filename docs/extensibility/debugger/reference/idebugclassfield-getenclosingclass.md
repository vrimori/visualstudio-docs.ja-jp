---
title: IDebugClassField::GetEnclosingClass |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 31bde98be596cdfca61434ecab3640655a8c7154
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49877128"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
このクラスの外側のクラスを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetEnclosingClass(   
   IDebugClassField** ppClassField  
);  
```  
  
```csharp  
int GetEnclosingClass(  
   out IDebugClassField ppClassField  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppClassField`  
 [out]返します、 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)オブジェクト、それを囲むを表すクラスします。 外側のクラスが存在しない場合は、null 値を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このクラスが表されている場合[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)オブジェクトが入れ子になったクラス、`ppClassField`パラメーターを返します、`IDebugClassField`オブジェクト、それを囲むを表すクラスします。 たとえば、このクラスの定義を考えてみます。  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 呼び出す、`GetEnclosingClass`メソッドを`IDebugClassField`オブジェクトを表す、`NestedClass`クラスを返します、`IDebugClassField`クラスを表すオブジェクト`RootClass`します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)