---
title: IEEVisualizerDataProvider::SetObjectForVisualizer |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f02f90ce8325a0ba75c31904a689e84705a5273a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49866169"
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
このメソッドは、ビジュアライザーを表すオブジェクトを変更します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetObjectForVisualizer(  
   IDebugObject*  pNewObject,  
   BSTR*          error,  
   IDebugObject** pException  
);  
```  
  
```csharp  
int SetObjectForVisualizer(  
   IDebugObject     pNewObject,  
   out string       error,  
   out IDebugObject pException  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pNewObject`  
 [in]設定するオブジェクト。  
  
 `error`  
 [out]オブジェクトを設定中にエラーがあった場合、この文字列は、エラー メッセージを保持します。  
  
 `pException`  
 [out]エラーがあった場合、このオブジェクトは、例外情報を保持します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 エラー情報を返す方法を決定する、実装者の責任です。 ただし、これはことを認識する例外オブジェクトが返されたかどうかにエラーが発生しました、エラーが発生した場合、このメソッドは例外オブジェクトを返す常にする必要がありますのでのみがいくつかの呼び出し元に可能性がありますができます。 エラー文字列は、呼び出し元が作成する場合も指定するのに使用します。  
  
## <a name="see-also"></a>関連項目  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)