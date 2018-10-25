---
title: IDebugSymbolProvider::GetMethodFieldsByName |Microsoft Docs
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
- IDebugSymbolProvider::GetMethodFieldsByName
helpviewer_keywords:
- IDebugSymbolProvider::GetMethodFieldsByName method
ms.assetid: 1f781320-81ef-4037-b068-f1864b271258
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 367dcd6648beb14e71de11fb542c6d401b0abcc4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49843471"
---
# <a name="idebugsymbolprovidergetmethodfieldsbyname"></a>IDebugSymbolProvider::GetMethodFieldsByName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このメソッドは、完全修飾メソッド名を表すフィールドを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetMethodFieldsByName(   
   LPCOLESTR          pszFullName,  
   NAME_MATCH         nameMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int GetMethodFieldsByName(  
   string               pszFullName,   
   NAME_MATCH           nameMatch,   
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pszFullName`  
 [in]メソッドの名前。  
  
 `nameMatch`  
 [in]たとえば、一致の大文字小文字を区別の種類を選択します。  
  
 `ppEnum`  
 [out]返します、 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)このメソッドに関連付けられているフィールドの列挙子。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 メソッドは、オーバー ロードされて、たとえば場合、複数のフィールドを関連付けることができます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)

