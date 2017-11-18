---
title: "IDebugDocumentContext インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugDocumentContext interface
ms.assetid: 665ee08a-5c6a-4ab1-ab93-de376acc9a74
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 432fbe9de5b1ab19c64ae1b9eeee36f3b1156d06
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumentcontext-interface"></a>IDebugDocumentContext インターフェイス
デバッグ中のドキュメントの一部の抽象表現を提供します。 テキスト ドキュメントのこの表現は、文字位置の範囲で構成されます。  
  
 継承されたメソッドだけでなく`IUnknown`、`IDebugDocumentContext`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugDocumentContext::GetDocument](../../winscript/reference/idebugdocumentcontext-getdocument.md)|このコンテキストを含むドキュメントを返します。|  
|[IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)|このドキュメントのコンテキストに関連付けられているコードのコンテキストを列挙します。|