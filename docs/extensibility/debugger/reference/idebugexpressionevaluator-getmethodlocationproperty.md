---
title: "IDebugExpressionEvaluator::GetMethodLocationProperty |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 592a3401d0f9712a78fcab9cf1056b05c6a746b8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/06/2017

---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
このメソッドは、メモリ アドレスに、メソッドの場所とオフセットを変換します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetMethodLocationProperty(   
   LPCOLESTR             upstrFullyQualifiedMethodPlusOffset,  
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   IDebugProperty2**     ppProperty  
);  
```  
  
```csharp  
int GetMethodLocationProperty(  
   string               upstrFullyQualifiedMethodPlusOffset,   
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   out IDebugProperty2  ppProperty  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `upstrFullyQualifiedMethodPlusOffset`  
 [in]オフセットとメソッドの場所は、文字列として表されます。  
  
 `pSymbolProvider`  
 [in]シンボル プロバイダーで表した、 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)オブジェクト。  
  
 `pAddress`  
 [in]表される、メソッド内のアドレス、 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)オブジェクト。  
  
 `pBinder`  
 [in]バインダーで表した、 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)オブジェクト。  
  
 `ppProperty`  
 [out]返します、 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)メモリ アドレスを表すインターフェイスです。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 たとえば、ブレークポイントを設定する、返されたアドレスを使用できます。  
  
 名前に関係なく`upstrFullyQualifiedMethodPlusOffset`、部分修飾メソッド名をこのパラメーターに渡すことができます。 その場合は、選択した方法であるを囲む`pAddress`です。 このパラメーターを解釈する方法は、式エバリュエーターとサポートする言語の実装によって異なります。  
  
## <a name="see-also"></a>関連項目  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
