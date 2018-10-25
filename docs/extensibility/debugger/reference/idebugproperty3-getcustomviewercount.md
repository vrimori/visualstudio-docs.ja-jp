---
title: IDebugProperty3::GetCustomViewerCount |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty3::GetCustomViewerCount
helpviewer_keywords:
- IDebugProperty3::GetCustomViewerCount
ms.assetid: dc5bb3e4-dc85-46e4-98fa-c6be8583b985
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1e609451af16d202828fac30cd0da133bf3bea73
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49898877"
---
# <a name="idebugproperty3getcustomviewercount"></a>IDebugProperty3::GetCustomViewerCount
このプロパティの使用可能な可能性があるカスタム ビューアーの数を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetCustomViewerCount(  
   ULONG* pcelt  
);  
```  
  
```csharp  
int GetCustomViewerCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pcelt`  
 [out]このプロパティの使用可能なカスタム ビューアーの数。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドが呼び出しを転送する型のビジュアライザーをサポートするために、 [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)メソッド。 式エバリュエーターでは、このプロパティの型のカスタム ビューアーもサポートする場合、このメソッドは、返された値のカスタム ビューアーの数を追加します。  
  
 型のビジュアライザーおよびカスタム ビューアーとの違いについての詳細については、次を参照してください。[型のビジュアライザーとカスタム ビューアー](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)します。  
  
## <a name="example"></a>例  
 次の例では、このメソッドを実装する方法を示しています、 **CProperty**を公開するオブジェクト、 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)インターフェイス。  
  
```cpp  
STDMETHODIMP CProperty::GetCustomViewerCount(ULONG* pcelt)  
{  
    if (pcelt == NULL)  
    {  
        return E_POINTER;  
    }  
  
    if (GetVisualizerService())  
    {  
        return m_pIEEVisualizerService->GetCustomViewerCount(pcelt);  
    }  
    else  
    {  
        return E_NOTIMPL;  
    }  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)   
 [型のビジュアライザーとカスタム ビューアー](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)