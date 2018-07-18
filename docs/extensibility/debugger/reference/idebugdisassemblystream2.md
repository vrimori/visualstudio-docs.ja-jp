---
title: IDebugDisassemblyStream2 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDisassemblyStream2
helpviewer_keywords:
- IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c1598ec8a6e5fca5275384c00433d74d22ce3505
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107895"
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
このインターフェイスは、命令のストリームを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugDisassemblyStream2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジンでは、プログラム コードの逆アセンブルをサポートするためにこのインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出し、 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)メソッドは、このインターフェイスを返します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugDisassemblyStream2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[読み取り](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|逆アセンブル ストリーム内の現在位置から開始する指示を読み取ります。|  
|[シーク](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|[逆アセンブル] ストリームを指定した位置を基準とした命令数が特定の読み取りのポインターを移動します。|  
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|特定のコードのコンテキストのコードの場所の識別子を返します。|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|指定されたコードの場所 id に対応するコード コンテキスト オブジェクトを返します。|  
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|現在のコードの場所を表すコード場所識別子を返します。|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|[逆アセンブル] のこのストリームに関連付けられているソース ドキュメントを取得します。|  
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|[逆アセンブル] のこのストリームのスコープを取得します。|  
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|[逆アセンブル] のこのストリームのサイズを取得します。|  
  
## <a name="remarks"></a>コメント  
 アドレス空間全体または単なる関数または領域内のモジュールを表すため、逆アセンブル ストリームを作成できます。 各命令がによって表される、 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)への呼び出しによって返される構造体、[読み取り](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)メソッドです。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)