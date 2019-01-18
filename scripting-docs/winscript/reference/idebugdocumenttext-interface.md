---
title: IDebugDocumentText インターフェイス |Microsoft Docs
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
ms.openlocfilehash: 763678b08c22fe34ec6ffebbe670fb8b50af6576
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344396"
---
# <a name="idebugdocumenttext-interface"></a>IDebugDocumentText インターフェイス
デバッグ ドキュメントのテキストのみのバージョンへのアクセスを提供します。 このインターフェイスは、次の規則を使用します。  
  
- 文字位置と行番号は、0 から始まるが。  
  
- 文字位置が文字のオフセットを表すバイトを表すやワード オフセットできません。 Win32 の文字位置は、Unicode オフセットです。  
  
  継承されたメソッドだけでなく`IDebugDocument`、`IDebugDocumentText`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugDocumentText::GetDocumentAttributes](../../winscript/reference/idebugdocumenttext-getdocumentattributes.md)|ドキュメントの属性を返します。|  
|[IDebugDocumentText::GetSize](../../winscript/reference/idebugdocumenttext-getsize.md)|文書内の行の数と文字数を返します。|  
|[IDebugDocumentText::GetPositionOfLine](../../winscript/reference/idebugdocumenttext-getpositionofline.md)|行の最初の文字に対応する文字位置を返します。|  
|[IDebugDocumentText::GetLineOfPosition](../../winscript/reference/idebugdocumenttext-getlineofposition.md)|指定した文字位置に行番号と、必要に応じて、対応する行内の文字オフセットを返します。|  
|[IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)|文字または文字位置の範囲に関連付けられている文字の属性を取得します。|  
|[IDebugDocumentText::GetPositionOfContext](../../winscript/reference/idebugdocumenttext-getpositionofcontext.md)|ドキュメントのコンテキストに対応する文字位置の範囲を返します。|  
|[IDebugDocumentText::GetContextOfPosition](../../winscript/reference/idebugdocumenttext-getcontextofposition.md)|指定された文字位置の範囲に対応するドキュメントのコンテキスト オブジェクトを作成します。|