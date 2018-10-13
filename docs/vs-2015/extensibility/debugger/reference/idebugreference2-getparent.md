---
title: IDebugReference2::GetParent |Microsoft Docs
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
- IDebugReference2::GetParent
helpviewer_keywords:
- IDebugReference2::GetParent
ms.assetid: e3061665-ad3e-4c1b-b33f-82755fa21be3
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3c56d3af5fab3fe4ac9d9621dcbe089b810e09d4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49257141"
---
# <a name="idebugreference2getparent"></a>IDebugReference2::GetParent
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

参照の親参照を取得します。 将来使用するために予約されています。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetParent (   
   IDebugReference2** ppParent  
);  
```  
  
```csharp  
int GetParent (   
   out IDebugReference2 ppParent  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppParent`  
 [out]返します、 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)このプロパティの親を表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 常に `E_NOTIMPL` を返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)

