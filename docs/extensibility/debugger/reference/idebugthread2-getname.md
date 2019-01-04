---
title: IDebugThread2::GetName |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugThread2::GetName
helpviewer_keywords:
- IDebugThread2::GetName
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d5d53d0e9a76caa1341494cea93311f9c912191c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53948681"
---
# <a name="idebugthread2getname"></a>IDebugThread2::GetName
スレッドの名前を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetName (   
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetName (   
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pbstrName`  
 [out]スレッドの名前を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 取得した名前が表示可能な名前で常に、この名前は、スレッドをについて説明します。 スレッド名は、実行時のアーキテクチャをサポートしていますが、スレッドをという名前またはデバッグ エンジンから派生した名前がありますから派生させることがあります。 呼び出してスレッドの名前を設定する代わりに、 [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)メソッド。  
  
## <a name="see-also"></a>関連項目  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)