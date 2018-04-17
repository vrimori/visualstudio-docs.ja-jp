---
title: IDebugObject::SetValue |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject::SetValue
helpviewer_keywords:
- IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ae6f8f589c0dca8c97e1a9664d9eaa93bf9e8741
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
連続する一連のバイトからオブジェクトの値を設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetValue(   
   BYTE* pValue,  
   UINT  nSize  
);  
```  
  
```csharp  
int SetValue(  
   byte[] pValue,   
   uint   nSize  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pValue`  
 [in]新しい値を表すバイトの配列。  
  
 `nSize`  
 [in]値をバイト単位のサイズ。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 配列内の値がこれにコピーされます[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)オブジェクト、既存の値を置換します。 新しい値のサイズは、既存の値より大きくまたは小さくできます。 これは、`IDebugObject`の参照を null にすることはできません。  
  
## <a name="see-also"></a>関連項目  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)