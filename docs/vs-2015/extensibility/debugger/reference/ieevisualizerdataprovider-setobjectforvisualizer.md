---
title: IEEVisualizerDataProvider::SetObjectForVisualizer |Microsoft Docs
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
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fdbd6ec439fc46b0ecab7621d4f793c1b3e33450
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893482"
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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

