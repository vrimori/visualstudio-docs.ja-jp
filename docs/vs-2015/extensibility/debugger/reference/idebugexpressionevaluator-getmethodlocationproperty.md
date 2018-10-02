---
title: IDebugExpressionEvaluator::GetMethodLocationProperty |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a11013ba2450685798796d0645486cf178950fc1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548912"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugExpressionEvaluator::GetMethodLocationProperty](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugexpressionevaluator-getmethodlocationproperty)します。  
  
このメソッドは、メモリ アドレスにメソッドの場所とオフセットを変換します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 [in]メソッドの場所とのオフセットは、文字列として表されます。  
  
 `pSymbolProvider`  
 [in]シンボル プロバイダーで表した、 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)オブジェクト。  
  
 `pAddress`  
 [in]表されるメソッド内のアドレス、 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)オブジェクト。  
  
 `pBinder`  
 [in]バインダーで表した、 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)オブジェクト。  
  
 `ppProperty`  
 [out]返します、 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)メモリ アドレスを表すインターフェイスです。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 たとえば、ブレークポイントを設定するのには、返されたアドレスを使用できます。  
  
 名前に関係なく`upstrFullyQualifiedMethodPlusOffset`、このパラメーターは、部分的に修飾メソッド名を渡すことができます。 選択したメソッドを囲む、1 つは、その場合は、`pAddress`します。 このパラメーターを解釈する方法は、式エバリュエーターと言語のサポートの実装の責任です。  
  
## <a name="see-also"></a>関連項目  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)

