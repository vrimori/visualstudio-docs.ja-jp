---
title: IEnumDebugThreads2::Clone |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugThreads2::Clone
helpviewer_keywords:
- IEnumDebugThreads2::Clone
ms.assetid: d774322c-e72d-4df3-b317-928da39dadc5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 25d8874b853b3d8930d99fa8f3099f22f2da9f4d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54957729"
---
# <a name="ienumdebugthreads2clone"></a>IEnumDebugThreads2::Clone
個別のオブジェクトとして現在の列挙体のコピーを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Clone(  
   IEnumDebugThreads2** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugThreads2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppEnum`  
 [out]個別のオブジェクトとして、この列挙体のコピーを返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 列挙体のコピーは、このメソッドが呼び出されたとき、元と同じ状態が。 ただし、コピーのと、元の状態は別であり、個別に変更することができます。  
  
## <a name="see-also"></a>関連項目  
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)