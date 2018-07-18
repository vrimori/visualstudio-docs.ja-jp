---
title: IDebugDisassemblyStream2::GetSize |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDisassemblyStream2::GetSize
helpviewer_keywords:
- IDebugDisassemblyStream2::GetSize
ms.assetid: 8f512704-12d0-46d2-959a-4f8dffe117b5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f43a0fe3d7d2ad7c54ee9203037595dade7c6486
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31106677"
---
# <a name="idebugdisassemblystream2getsize"></a>IDebugDisassemblyStream2::GetSize
[逆アセンブル] のこのストリームの手順で、サイズを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetSize(   
   UINT64* pnSize  
);  
```  
  
```csharp  
int GetSize(   
   out ulong pnSize  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pnSize`  
 [out]手順で、サイズを返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 配列を割り当てるには、このメソッドから返される値を使用できます[DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)構造体に渡され、[読み取り](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)メソッドです。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [読み取り](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)