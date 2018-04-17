---
title: IDebugClassField::GetEnclosingClass |Microsoft ドキュメント
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
ms.openlocfilehash: 6cd73955835f8aff0047995a690da03e5ab0305d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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
 [out]返します、 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)包含を表すオブジェクトのクラスです。 外側のクラスが存在しない場合は、null 値を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 このクラスが表されている場合[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)オブジェクトは、入れ子になったクラス、`ppClassField`パラメーターを返します、`IDebugClassField`包含を表すオブジェクトのクラスです。 たとえば、次のクラス定義を考えてみます。  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 呼び出す、`GetEnclosingClass`メソッドを`IDebugClassField`オブジェクトを表す、`NestedClass`クラスを返します、`IDebugClassField`クラスを表すオブジェクトを`RootClass`です。  
  
## <a name="see-also"></a>関連項目  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)