---
title: IEnumDebugAddresses::GetCount |Microsoft Docs
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
- IEnumDebugAddresses::GetCount
helpviewer_keywords:
- IEnumDebugAddresses::GetCount method
ms.assetid: f2ca8ff8-539f-457c-83f8-9bbf97618065
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 974049131e0a016168b591af2fd15d8e8994d26f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49187132"
---
# <a name="ienumdebugaddressesgetcount"></a>IEnumDebugAddresses::GetCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このメソッドは、列挙体の要素の数を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetCount(  
   [out] ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pcelt`  
 [out]列挙体の要素の数を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、[次へ]、複製、スキップ、およびリセットを実装する必要があることを指定する、よく使用される列挙型の COM インターフェイスの一部ではありません。  
  
## <a name="see-also"></a>関連項目  
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)

