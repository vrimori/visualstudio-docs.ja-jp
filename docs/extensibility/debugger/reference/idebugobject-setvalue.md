---
title: "IDebugObject::SetValue |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugObject::SetValue
helpviewer_keywords:
- IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 7249c2bc64afea2ca1037cc7fa1cf617357341d7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

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
