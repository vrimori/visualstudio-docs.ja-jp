---
title: "IEEVisualizerDataProvider::SetObjectForVisualizer |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: feb48452b466301f7987db613997158aed160bac
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
 [out]エラーがあった場合、このオブジェクトは、例外情報を格納します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 エラー情報を返す方法を決定する、実装者の責任です。 ただし、可能であればだけで認識に、例外オブジェクトが返されたかどうかにエラーが発生しました、エラーが発生した場合、このメソッドは例外オブジェクトを返す常にする必要がありますのでがいくつかの呼び出し元に可能性があります。 エラー文字列は、呼び出し元がようにしたい場合にも指定するのに使用します。  
  
## <a name="see-also"></a>参照  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)