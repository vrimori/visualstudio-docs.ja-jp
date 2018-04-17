---
title: IDebugArrayObject::GetElement |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e2e10eced58835044220da0650712dacb131ada3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugarrayobjectgetelement"></a>IDebugArrayObject::GetElement
配列の要素を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetElement(   
   DWORD          dwIndex,  
   IDebugObject** ppElement  
);  
```  
  
```csharp  
int GetElement(  
   [In] uint dwIndex,   
   out IDebugObject ppElement  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwIndex`  
 [in]要素のインデックス。  
  
 `ppElement`  
 [out]返します、 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)要素を表すインターフェイス。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 このメソッドは、1 次元の配列として、配列オブジェクトがマルチ ディメンションの場合でもすべての要素の配列オブジェクトのように表示されます。 などの配列を指定して`myarray[3][2][6]`と`dwIndex`20 のパラメーターは、このメソッドは、要素から`myarray[1][1][2]`、および`dwIndex`21 のパラメーターは元の要素を返します`myarray[1][1][3]`です。 使用して、 [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)配列内の要素の合計数を調べます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)