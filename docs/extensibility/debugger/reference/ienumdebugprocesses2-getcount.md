---
title: IEnumDebugProcesses2::GetCount |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugProcesses2::GetCount
helpviewer_keywords:
- IEnumDebugProcesses2::GetCount
ms.assetid: 5dc3e36c-46e5-4556-bf41-1870aa67d2a0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 157a4ce51d0bac693296a7b0ae55b7959b8c686d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53857868"
---
# <a name="ienumdebugprocesses2getcount"></a>IEnumDebugProcesses2::GetCount
列挙体の要素の数を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetCount(  
   ULONG* pcelt  
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
 このメソッドだけを指定する、よく使用される列挙型の COM インターフェイスの一部でない、 `Next`、 `Clone`、 `Skip`、および`Reset`メソッドを実装する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)