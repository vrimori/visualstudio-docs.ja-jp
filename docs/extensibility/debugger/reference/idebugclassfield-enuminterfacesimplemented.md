---
title: "IDebugClassField::EnumInterfacesImplemented |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords:
- IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
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
ms.openlocfilehash: 94d35194abdacc8cb07ee39c0d401be825b63277
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="idebugclassfieldenuminterfacesimplemented"></a>IDebugClassField::EnumInterfacesImplemented
このクラスで実装されたインターフェイスの列挙子を作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumInterfacesImplemented(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumInterfacesImplemented(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppEnum`  
 [out]返します、 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)実装されたインターフェイスのリストを表すオブジェクト。 インターフェイスがない場合は、null 値を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。 または、このクラスで実装されたインターフェイスが存在しない場合は S_FALSE を返します。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 列挙体の各要素は、 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)インターフェイスを記述するオブジェクト。 アンマネージ注[!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)]ため、このメソッドは、アンマネージについて常に null 値を返します、コードが不連続エンティティとしてインターフェイスを使用しない[!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)]コード。  
  
## <a name="see-also"></a>関連項目  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
