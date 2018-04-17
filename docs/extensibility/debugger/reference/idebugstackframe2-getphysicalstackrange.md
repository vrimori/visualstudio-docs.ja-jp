---
title: IDebugStackFrame2::GetPhysicalStackRange |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: be53b50bc21d81c60f7131e8ed437ecb2ac2f16c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
スタック フレームに関連付けられている物理アドレスの範囲のコンピューターに依存する形式を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetPhysicalStackRange (   
   UINT64* paddrMin,  
   UINT64* paddrMax  
);  
```  
  
```csharp  
int GetPhysicalStackRange (   
   out ulong paddrMin,  
   out ulong paddrMax  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `paddrMin`  
 [out]このスタック フレームに関連付けられている最下位の物理アドレスを返します。  
  
 `paddrMax`  
 [out]このスタック フレームに関連付けられている最上位の物理アドレスを返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 このメソッドによって返される情報は、スタック フレームを並べ替え、セッション デバッグ マネージャー (SDM) によって使用されます。  
  
 呼び出し履歴が、ダウンされている拡張する、新しいスタック フレームがますます下位メモリ アドレスに追加されると見なされます。 実行時のアーキテクチャでは、この想定を一致する物理的なスタック範囲を提供する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)