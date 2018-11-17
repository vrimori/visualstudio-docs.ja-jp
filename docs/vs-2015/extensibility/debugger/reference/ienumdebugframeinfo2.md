---
title: IEnumDebugFrameInfo2 |Microsoft Docs
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
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6938641b2ec274d23928742bbaa014c43c02dc48
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51728276"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)

