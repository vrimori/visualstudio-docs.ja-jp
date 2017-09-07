---
title: "IDebugContainerField::EnumFields |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
caps.latest.revision: 10
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
ms.openlocfilehash: 1244306cbdfa70b0885274df75a7bf51a063bc30
ms.contentlocale: ja-jp
ms.lasthandoff: 09/06/2017

---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
コンテナーのフィールドの列挙子を作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumFields(   
   FIELD_KIND         dwKindFilter,  
   FIELD_MODIFIERS    dwModifiersFilter,  
   LPCOLESTR          pszNameFilter,  
   NAME_MATCH         nameMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumFields(  
   enum_ FIELD_KIND      dwKindFilter,   
   enum_ FIELD_MODIFIERS dwModifiersFilter,   
   string                pszNameFilter,   
   NAME_MATCH            nameMatch,   
   out IEnumDebugFields  ppEnum  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwKindFilter`  
 [in]組み合わせた[FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)列挙されるフィールドを選択する定数。 フィールドの種類は、記憶域の種類、クラスまたはプリミティブ型、または特定の情報など、ローカル、パラメーター、または"this"ポインターなどを記述できます。  
  
 `dwModifiersFilter`  
 [in]組み合わせた[FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)列挙されるフィールドを選択する定数。 フィールド修飾子は、パブリックまたはプライベート、または記憶域については、virtual、static、または最終などなどのアクセス許可を指定できます。  
  
 `pszNameFilter`  
 [in]列挙されるフィールドの名前。 すべてのフィールドが返される場合は、null 値にできます。  
  
 `nameMatch`  
 [in]値、 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)を検索するかどうかを制御する列挙体があるか大文字小文字を区別します。  
  
 `ppEnum`  
 [out]返します、 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)フィールドの一覧を表すオブジェクト。 フィールドが存在しない場合は、null 値を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合は、S_OK または S_FALSE をフィールドが存在しない場合は、返します。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 `dwKindFilter`、 `dwModifiersFilter`、および`pszNameFilter`パラメーターを組み合わせて、たとえば、すべてのパブリック仮想メソッドを"MyMethod"という名前を選択します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
