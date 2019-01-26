---
title: IDebugObject::SetValue |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugObject::SetValue
helpviewer_keywords:
- IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ba9b3983f3d6cab2525c391153457d362d2ad05
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55038397"
---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
連続した一連のバイトから、オブジェクトの値を設定します。  
  
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
  
## <a name="remarks"></a>Remarks  
 配列内の値は、これにコピーされます[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)既存の値を置き換えるオブジェクト。 新しい値のサイズは、既存の値より大きくまたは小さくできます。 これは、`IDebugObject`の参照を null にすることはできません。  
  
## <a name="see-also"></a>関連項目  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)