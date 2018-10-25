---
title: IDebugArrayField::GetRank |Microsoft Docs
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
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 162bb52a557e983b8616e4662ddcdd0976496105
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49814335"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

ランクの配列の次元数を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetRank(   
   DWORD* pdwRank  
);  
```  
  
```csharp  
int GetRank(  
   out uint pdwRank  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pdwRank`  
 [out]順位を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 配列のランクは、ディメンションの数に対応します。 C++ および C# の場合、多次元配列、配列の配列で実際には、1 次元の配列だけを考慮するそのためことができます (および`GetRank`メソッドは常に 1 を返します)。 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]、その一方で、多次元配列は異なる方法で処理およびそのような配列のランクには、ディメンションの数が反映されます (および`GetRank`メソッドは常にディメンションの数を返します)。  
  
## <a name="see-also"></a>関連項目  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)

