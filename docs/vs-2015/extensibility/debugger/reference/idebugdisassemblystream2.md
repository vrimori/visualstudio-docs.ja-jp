---
title: IDebugDisassemblyStream2 |Microsoft Docs
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
- IDebugDisassemblyStream2
helpviewer_keywords:
- IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 81210da4d743daac980a363e817b05fe8e3a11f3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49286820"
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このインターフェイスは、命令のストリームを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugDisassemblyStream2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジンでは、プログラムのコードの混合モードをサポートするには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出し、 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)メソッドは、このインターフェイスを返します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugDisassemblyStream2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|手順については、混合モードのストリームの現在位置から始まるを読み取ります。|  
|[Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|[逆アセンブル] ストリームの指定した位置の基準とした命令数が特定の読み取りポインターを移動します。|  
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|特定のコード コンテキストのコードの場所の識別子を返します。|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|指定したコードの場所の識別子に対応するコードのコンテキスト オブジェクトを返します。|  
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|現在のコードの場所を表すコードの場所の識別子を返します。|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|この混合モードのストリームに関連付けられているソース ドキュメントを取得します。|  
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|この混合モードのストリームのスコープを取得します。|  
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|この混合モードのストリームのサイズを取得します。|  
  
## <a name="remarks"></a>Remarks  
 アドレス空間全体だけ関数または領域内のモジュールを表すため、逆アセンブリのストリームを作成できます。 それぞれの命令がによって表される、 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)への呼び出しによって返される構造体、[読み取り](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)メソッド。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)

