---
title: IDebugDocumentPositionOffset2 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d10c71340b6ad6c7e76753b40c3bef55d8e7e606
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537936"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugDocumentPositionOffset2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdocumentpositionoffset2)します。  
  
文字のオフセットとしてソース ファイル内の位置を表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugDocumentPositionOffset2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 IDE によって実装され、デバッグ エンジンで使用します。  
  
## <a name="methods"></a>メソッド  
 次の表は、メソッドの`IDebugDocumentPositionOffset2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|現在のドキュメントの位置の範囲を取得します。|  
  
## <a name="remarks"></a>Remarks  
 同じ情報が返されます[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)が`char`ドキュメントの先頭からのオフセットします。 これによりは存在して、ディスクには、通常返される行と列の情報ではなく、文字の 1 次元配列と同様に、ドキュメントを表示します。  
  
## <a name="requirements"></a>要件  
 ヘッダー: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)

