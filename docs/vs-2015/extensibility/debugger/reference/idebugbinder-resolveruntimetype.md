---
title: IDebugBinder::ResolveRuntimeType |Microsoft Docs
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
- IDebugBinder::ResolveRuntimeType
helpviewer_keywords:
- IDebugBinder::ResolveRuntimeType method
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 40add50e343b7782e059aa726ebde4c4739366c8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825219"
---
# <a name="idebugbinderresolveruntimetype"></a>IDebugBinder::ResolveRuntimeType
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このメソッドは、オブジェクトの実行時の型を決定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT ResolveRuntimeType(   
   IDebugObject* pObject,  
   IDebugField** ppResolved  
);  
```  
  
```csharp  
int ResolveRuntimeType(  
   IDebugObject     pObject,   
   out IDebugField  ppResolved  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pObject`  
 [in][IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)を解決できます。  
  
 `ppResolved`  
 [out]オブジェクトの型を返します、 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 オブジェクトの実行時の型はコンパイル時に常には認識されません。 たとえば、ポリモーフィズムを使用して、引数ことができます関数として渡すボタン クラスなど、基本クラス。 実際の引数は、ラジオ ボタン クラスなどの派生クラスで可能性があります。  
  
## <a name="see-also"></a>関連項目  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

