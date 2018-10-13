---
title: IDebugMemoryContext2::GetName |Microsoft Docs
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
- IDebugMemoryContext2::GetName
helpviewer_keywords:
- IDebugMemoryContext2::GetName method
- GetName method
ms.assetid: 8c212556-7d9e-4d68-b2a9-8212f50d0287
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8e61e0a075b414d09b7e5510bd18440a5e7b4dfc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49299248"
---
# <a name="idebugmemorycontext2getname"></a>IDebugMemoryContext2::GetName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このコンテキストの表示名を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetName(   
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetName(  
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pbstrName`  
 [out]メモリのコンテキストの名前を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 メモリのコンテキストの名前は、通常使用されません。  
  
## <a name="see-also"></a>関連項目  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)

