---
title: "IDebugClassField::GetEnclosingClass |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugClassField::GetEnclosingClass
helpviewer_keywords: IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fbec5ac48280cf10bc89e73faca0779384bf3549
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
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