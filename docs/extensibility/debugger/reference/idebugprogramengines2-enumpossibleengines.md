---
title: "IDebugProgramEngines2::EnumPossibleEngines |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords: IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d1cf3eead4b268dbbca5ad4333adcc647522b051
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
すべての使用可能なデバッグ エンジン (DE) このプログラムをデバッグできる対応する Guid を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumPossibleEngines(   
   DWORD  celtBuffer,  
   GUID*  rgguidEngines,  
   DWORD* pceltEngines  
);  
```  
  
```csharp  
int EnumPossibleEngines(   
   uint      celtBuffer,  
   GUID[]    rgguidEngines,  
   ref DWORD pceltEngines  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `celtBuffer`  
 [in]返す DE Guid の数。 これも、最大のサイズを指定、`rgguidEngines`配列。  
  
 `rgguidEngines`  
 [入力、出力].格納する DE Guid の配列。  
  
 `pceltEngines`  
 [out]返される DE Guid の実際の数を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。 [C++] が返されます`HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)`または [c#] 0x8007007A、バッファーの大きさがない場合。  
  
## <a name="remarks"></a>コメント  
 エンジンの数を決定するためにこのメソッドが 1 回、`celtBuffer`パラメーター 0 に設定され、`rgguidEngines`パラメーターが null の値に設定します。 返されます。 `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` (0x8007007A C# の場合)、および`pceltEngines`パラメーターが必要とするバッファーのサイズを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)