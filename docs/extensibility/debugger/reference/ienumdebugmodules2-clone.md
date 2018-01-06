---
title: "IEnumDebugModules2::Clone |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugModules2::Clone
helpviewer_keywords: IEnumDebugModules2::Clone
ms.assetid: fd6d3abc-20d9-4f6f-9c8e-5bd29f68d47d
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4ec6c6f14824357da9f8a0d1ae9dd74c9124a377
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugmodules2clone"></a>IEnumDebugModules2::Clone
個別のオブジェクトとして現在の列挙型のコピーを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Clone(  
   IEnumDebugModules2** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugModules2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppEnum`  
 [out]個別のオブジェクトとしてこの列挙体のコピーを返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 列挙体のコピーでは、このメソッドが呼び出されたときに元と同じ状態がします。 ただし、コピーのと、元の状態は別に、個別に変更することができます。  
  
## <a name="see-also"></a>参照  
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)