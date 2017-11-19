---
title: "IEnumDebugFields::Reset |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugFields::Reset
helpviewer_keywords: IEnumDebugFields::Reset method
ms.assetid: 38ff61e4-0120-42e8-971a-16be6050b425
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2d443f7b5530349663f8e8fdf63c7ed042a1d2da
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugfieldsreset"></a>IEnumDebugFields::Reset
このメソッドは、最初の要素に列挙体をリセットします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Reset(void);  
```  
  
```csharp  
int Reset();  
```  
  
#### <a name="parameters"></a>パラメーター  
 なし  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 このメソッドが呼び出された後、次の呼び出し[次](../../../extensibility/debugger/reference/ienumdebugfields-next.md)列挙体の最初の要素を返します。  
  
## <a name="see-also"></a>関連項目  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [次へ](../../../extensibility/debugger/reference/ienumdebugfields-next.md)