---
title: "IDebugDocumentText インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugDocumentText インターフェイス"
ms.assetid: 242bad79-9c0a-4a30-879a-9f43db4e022b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText インターフェイス
デバッグのドキュメントのテキストのみのバージョンへのアクセスを提供します。  このインターフェイスは、次の規則を使用します:  
  
-   文字の位置と行番号は、ゼロです。  
  
-   文字位置は、文字のオフセットを表します; これらはバイトまたは Word のオフセットを表します。  Win32 の場合、は Unicode 文字位置のオフセットです。  
  
 `IDebugDocument` から継承するメソッドに加え、`IDebugDocumentText` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IDebugDocumentText::GetDocumentAttributes](../../winscript/reference/idebugdocumenttext-getdocumentattributes.md)|ドキュメントの属性を返します。|  
|[IDebugDocumentText::GetSize](../../winscript/reference/idebugdocumenttext-getsize.md)|行数とドキュメントの文字数を返します。|  
|[IDebugDocumentText::GetPositionOfLine](../../winscript/reference/idebugdocumenttext-getpositionofline.md)|行の最初の文字に対応する文字位置を返します。|  
|[IDebugDocumentText::GetLineOfPosition](../../winscript/reference/idebugdocumenttext-getlineofposition.md)|特定の文字位置に対応する行内の行番号と、オプションで、文字のオフセットを返します。|  
|[IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)|文字位置の範囲に関連付けられた文字や文字の属性を取得します。|  
|[IDebugDocumentText::GetPositionOfContext](../../winscript/reference/idebugdocumenttext-getpositionofcontext.md)|ドキュメントのコンテキストに対応する文字位置の範囲を返します。|  
|[IDebugDocumentText::GetContextOfPosition](../../winscript/reference/idebugdocumenttext-getcontextofposition.md)|指定された文字位置の範囲に対応するドキュメントのコンテキスト オブジェクトを作成します。|