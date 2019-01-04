---
title: IEnumDebugFrameInfo2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: aa2db1f249492702971eb311fe38f76eec3a5b3b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53857201"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
このインターフェイスの列挙[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)構造体。  
  
## <a name="syntax"></a>構文  
  
```  
IEnumDebugFrameInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) は、現在の呼び出し履歴を記述する構造体のリストを提供するには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 Visual Studio 呼び出し[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)例外、または停止がデバッグ中のプログラムで発生するたびに、ブレークポイントは、このインターフェイスを取得します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IEnumDebugFrameInfo2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[次へ](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|指定した数を取得[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)列挙体シーケンス内の構造体。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|指定した数のスキップ[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)列挙体シーケンス内の構造体。|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|先頭に、列挙体シーケンスをリセットします。|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|現在の列挙子と同じ列挙状態を格納する列挙子を作成します。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|数を取得[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)列挙子内の構造体。|  
  
## <a name="remarks"></a>Remarks  
 Visual Studio は、ブレークポイント、例外、またはデバッグ中のプログラムの一時停止をユーザーが生成したを処理する最初の手順として、このインターフェイスを取得します。 一連の[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)構造体が現在の呼び出し履歴を表す、一覧と、最も古い関数の先頭には、現在の関数呼び出しで、一覧の最後に呼び出します。 各`FRAMEINFO`コンテキストは、式を評価して、ローカル変数を調べる、スタック フレームを表します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)