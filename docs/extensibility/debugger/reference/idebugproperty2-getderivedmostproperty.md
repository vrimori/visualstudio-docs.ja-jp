---
title: "IDebugProperty2::GetDerivedMostProperty |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty2::GetDerivedMostProperty
helpviewer_keywords: IDebugProperty2::GetDerivedMostProperty
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4e9efd498485340b49dbd385a6a94fa6cf7fcedd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugproperty2getderivedmostproperty"></a>IDebugProperty2::GetDerivedMostProperty
プロパティの最派生プロパティを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetDerivedMostProperty (   
   IDebugProperty2** ppDerivedMost  
);  
```  
  
```csharp  
int GetDerivedMostProperty (   
   out IDebugProperty2 ppDerivedMost  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppDerivedMost`  
 [out]返します、 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)最派生プロパティを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`; エラー コードを返しますそれ以外の場合。 返します`S_GETDERIVEDMOST_NO_DERIVED_MOST`最派生取得するプロパティが存在しない場合。  
  
## <a name="remarks"></a>コメント  
 たとえば、このプロパティを実装するオブジェクトの説明`ClassRoot`がのインスタンス化では実際には、`ClassDerived`から派生する`ClassRoot`、このメソッドから返されます、 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)オブジェクト記述する、`ClassDerived`オブジェクト。  
  
## <a name="see-also"></a>参照  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)