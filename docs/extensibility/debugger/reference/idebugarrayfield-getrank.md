---
title: "IDebugArrayField::GetRank |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugArrayField::GetRank
helpviewer_keywords: IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2467c8d4ed85a685de80511d68a20e24c047306e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
ランクまたは配列の次元数を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
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
  
## <a name="remarks"></a>コメント  
 配列のランクは、ディメンションの数に対応します。 C++ および C# の場合、多次元配列は配列の配列で、実際には、したがって対象となる 1 次元配列のみ (および`GetRank`メソッドは常に 1 を返します)。 [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]、その一方で、多次元配列の異なる方法で処理およびそのような配列のランクがディメンションの数を表します (および`GetRank`メソッドは常にディメンションの数を返します)。  
  
## <a name="see-also"></a>関連項目  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)