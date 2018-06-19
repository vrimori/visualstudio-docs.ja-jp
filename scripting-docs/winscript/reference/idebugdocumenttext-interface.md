---
title: IDebugDocumentText インターフェイス |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentText interface
ms.assetid: 242bad79-9c0a-4a30-879a-9f43db4e022b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9522d1075cd796fb69f6abbc42adc2706a817fed
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727952"
---
# <a name="idebugdocumenttext-interface"></a>IDebugDocumentText インターフェイス
デバッグのドキュメントのテキストのみのバージョンへのアクセスを提供します。 このインターフェイスは、次の規則を使用します。  
  
-   文字位置と行番号は、0 から始まるがします。  
  
-   文字位置を表す文字オフセットです。バイトを表すまたはワード オフセットいません。 Win32、文字位置は、Unicode オフセットです。  
  
 継承されたメソッドだけでなく`IDebugDocument`、`IDebugDocumentText`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugDocumentText::GetDocumentAttributes](../../winscript/reference/idebugdocumenttext-getdocumentattributes.md)|ドキュメントの属性を返します。|  
|[IDebugDocumentText::GetSize](../../winscript/reference/idebugdocumenttext-getsize.md)|ドキュメント内の行の数と文字数を返します。|  
|[IDebugDocumentText::GetPositionOfLine](../../winscript/reference/idebugdocumenttext-getpositionofline.md)|行の最初の文字に対応する文字位置を返します。|  
|[IDebugDocumentText::GetLineOfPosition](../../winscript/reference/idebugdocumenttext-getlineofposition.md)|指定した文字位置に行番号と、必要に応じて、対応する行内の文字オフセットを返します。|  
|[IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)|文字または文字位置の範囲に関連付けられた文字属性を取得します。|  
|[IDebugDocumentText::GetPositionOfContext](../../winscript/reference/idebugdocumenttext-getpositionofcontext.md)|ドキュメントのコンテキストに対応する文字位置の範囲を返します。|  
|[IDebugDocumentText::GetContextOfPosition](../../winscript/reference/idebugdocumenttext-getcontextofposition.md)|指定された文字位置の範囲に対応するドキュメントのコンテキスト オブジェクトを作成します。|