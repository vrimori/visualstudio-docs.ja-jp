---
title: "IEnumDebugPrograms2::Clone |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumDebugPrograms2::Clone
helpviewer_keywords:
- IEnumDebugPrograms2::Clone
ms.assetid: 880846c2-39d3-45cd-85c3-ad5409a3710f
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
ms.openlocfilehash: 31d655aee812dd76df925ae98eea79e60f12286a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/06/2017

---
# <a name="ienumdebugprograms2clone"></a>IEnumDebugPrograms2::Clone
個別のオブジェクトとして現在の列挙型のコピーを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Clone(  
   IEnumDebugPrograms2** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugPrograms2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppEnum`  
 [out]個別のオブジェクトとしてこの列挙体のコピーを返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 列挙体のコピーでは、このメソッドが呼び出されたときに元と同じ状態がします。 ただし、コピーのと、元の状態は別に、個別に変更することができます。  
  
## <a name="see-also"></a>関連項目  
 [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)
