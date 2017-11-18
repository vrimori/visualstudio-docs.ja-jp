---
title: "コンテキストを文書化 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5a38d0ad28ad01b9e106cf06127b934dedfe5bba
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="document-context"></a>ドキュメントのコンテキスト
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 、デバッグ、**ドキュメントのコンテキスト**:  
  
-   ソース ファイル内の位置を表します。 言語のソース ファイルが存在していない可能性がある場合は、ドキュメントのコンテキストは、通常、実行時環境で生成されるドキュメント内の位置を識別します。 たとえば、スクリプト エンジンでは、スクリプトから、ドキュメントを生成する可能性があります。 詳細については、次を参照してください。[ドキュメントの位置](../../extensibility/debugger/document-position.md)です。  
  
-   コードのコンテキストに対応するソース ドキュメント内の位置をについて説明します。 シンボル ハンドラーは、コードのコンテキストをコンパイラまたはインタープリターによって生成される情報を使用して、ドキュメントのコンテキストにマップします。  
  
-   によって実装される、 [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md)インターフェイスです。  
  
## <a name="see-also"></a>関連項目  
 [コード コンテキスト](../../extensibility/debugger/code-context.md)   
 [プロバイダーのシンボル](../../extensibility/debugger/symbol-provider.md)   
 [シンボル プロバイダー インターフェイス](../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [デバッガー コンテキスト](../../extensibility/debugger/debugger-contexts.md)