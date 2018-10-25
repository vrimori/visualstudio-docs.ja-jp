---
title: IDebugAlias::GetICorDebugValue |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 97bc29454cde9c8ebe431ee1efff80e66cd9ed44
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49951406"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このエイリアスに関連付けられている値を表すマネージ コード インターフェイスを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```csharp  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppUnk`  
 [out]`IUnknown`このエイリアスに関連付けられている値を表すインターフェイスです。 このインターフェイスを照会できます、`ICorDebugValue`インターフェイス。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、管理対象の値のみに適用されます (、`ICorDebugValue`インターフェイスでは、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]で定義されていると、 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK では cordebug.idl ファイル)。  
  
## <a name="see-also"></a>関連項目  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)

