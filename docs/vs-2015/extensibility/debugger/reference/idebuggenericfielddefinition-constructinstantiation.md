---
title: IDebugGenericFieldDefinition::ConstructInstantiation |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ConstructInstantiation
- IDebugGenericFieldDefinition::ConstructInstantiation
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8c5bd1d6164019414bc7cc299e418c38365dbc95
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548071"
---
# <a name="idebuggenericfielddefinitionconstructinstantiation"></a>IDebugGenericFieldDefinition::ConstructInstantiation
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugGenericFieldDefinition::ConstructInstantiation](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebuggenericfielddefinition-constructinstantiation)します。  
  
型引数の配列を指定したフィールドのインスタンスを構築します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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

