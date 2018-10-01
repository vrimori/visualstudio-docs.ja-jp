---
title: IEnumDebugCustomAttributes::Skip |Microsoft Docs
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
- IEnumCustomAttributes::Skip
helpviewer_keywords:
- IEnumDebugCustomAttributes::Skip
ms.assetid: 54c72e23-cd4c-4746-935c-abea8057dd1b
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bb86f8d57ba4ee69c6d16c1e07c1baaff916f021
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533875"
---
# <a name="ienumdebugcustomattributesskip"></a>IEnumDebugCustomAttributes::Skip
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IEnumDebugCustomAttributes::Skip](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugcustomattributes-skip)します。  
  
指定された数の列挙体シーケンス内のカスタム属性をスキップします。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
```csharp  
int Skip(  
   uint celt  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `celt`  
 [in]スキップする要素の数。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`します。 返します`S_FALSE`場合`celt`が残りの要素の数より大きい。 それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 場合`celt`数より大きい値を指定します。 残りの要素の列挙体が最後に設定し、`S_FALSE`が返されます。  
  
## <a name="see-also"></a>関連項目  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)

