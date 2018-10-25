---
title: IDebugObject::SetValue |Microsoft Docs
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
ms.openlocfilehash: f1b78a4513aab8a9c4d2c539a592799dffdcea53
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49850972"
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