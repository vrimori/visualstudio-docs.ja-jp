---
title: IDebugGenericFieldDefinition::ConstructInstantiation |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ConstructInstantiation
- IDebugGenericFieldDefinition::ConstructInstantiation
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 83284124f4cdf2fce49812998b6444fa43dc958e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54954944"
---
# <a name="idebuggenericfielddefinitionconstructinstantiation"></a>IDebugGenericFieldDefinition::ConstructInstantiation
型引数の配列を指定したフィールドのインスタンスを構築します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ConstructInstantiation(  
   ULONG32       cArgs,  
   IDebugField** ppArgs,  
   IDebugField** ppConstructedField  
);  
```  
  
```csharp  
int ConstructInstantiation(  
   uint            cArgs,  
   IDebugField[]   ppArgs,  
   out IDebugField ppConstructedField  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `cArgs`  
 [in]引数の数、`ppArgs`配列。  
  
 `ppArgs`  
 [in]型引数を格納する配列。 型引数はクローズ型 (非ジェネリックまたは完全にインスタンス化されたジェネリック) である必要があります。  
  
 `ppConstructedField`  
 [out]返します、 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)新しいフィールドを表すインターフェイスです。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 制約がチェックされません。  
  
## <a name="see-also"></a>関連項目  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)