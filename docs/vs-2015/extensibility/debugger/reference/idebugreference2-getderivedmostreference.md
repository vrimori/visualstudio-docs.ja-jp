---
title: IDebugReference2::GetDerivedMostReference |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6b680571bc2edc54e89b1625b012e5a34885ffe9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47544382"
---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugReference2::GetDerivedMostReference](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugreference2-getderivedmostreference)します。  
  
参照の最派生参照を取得します。 将来使用するために予約されています。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetDerivedMostReference(   
   IDebugReference2** ppDerivedMost  
);  
```  
  
```csharp  
int GetDerivedMostReference(   
   out IDebugReference2 ppDerivedMost  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppDerivedMost`  
 [out]返します、 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)最派生プロパティを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 常に `E_NOTIMPL` を返します。  
  
## <a name="remarks"></a>Remarks  
 たとえば、このプロパティを実装するオブジェクトを記述する`ClassRoot`がのインスタンス化では実際には、`ClassDerived`から派生する`ClassRoot`、このメソッドから返されます、 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)オブジェクト参照を表す、`ClassDerived`オブジェクト。  
  
## <a name="see-also"></a>関連項目  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)

