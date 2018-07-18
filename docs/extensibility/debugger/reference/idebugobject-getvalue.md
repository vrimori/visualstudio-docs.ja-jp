---
title: IDebugObject::GetValue |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 50f65cba807abf4e8a0d7bc85ed28c765f7c6849
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31112517"
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
連続する一連のバイトとしてオブジェクトの値を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetValue(   
   BYTE* pValue,  
   UINT  nSize  
);  
```  
  
```csharp  
int GetValue(  
   ref byte[] pValue,   
   uint nSize  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pValue`  
 [入力、出力].される連続した一連のオブジェクトの値を表すバイト配列。  
  
 `nSize`  
 [in]フェッチするバイトの最大数。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 呼び出すことによってフェッチすることがある値のバイトの合計数を取得、 [GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)メソッドです。  
  
## <a name="see-also"></a>関連項目  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)