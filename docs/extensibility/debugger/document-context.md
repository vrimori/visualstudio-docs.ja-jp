---
title: "コンテキストを文書化 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 8ed5498961a575d0f9d3f7c64b46bc73a2d510b5
ms.lasthandoff: 02/22/2017

---
# <a name="document-context"></a>ドキュメントのコンテキスト
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 、デバッグ、**ドキュメントのコンテキスト**:  
  
-   ソース ファイル内の位置を表します。 言語のソース ファイルが存在していない可能性がある場合は、ドキュメントのコンテキストは、通常、実行時の環境で生成されるドキュメント内の位置を識別します。 たとえば、スクリプト エンジンでは、スクリプトからドキュメントを生成する可能性があります。 詳細については、次を参照してください。[ドキュメントの位置](../../extensibility/debugger/document-position.md)します。  
  
-   コードのコンテキストに対応するソース ドキュメント内の位置について説明します。 シンボルのハンドラーは、コードのコンテキストをコンパイラやインタープリターによって生成される情報を使用して、ドキュメントのコンテキストにマップします。  
  
-   によって実装される、 [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md)インターフェイスです。  
  
## <a name="see-also"></a>関連項目  
 [コードのコンテキスト](../../extensibility/debugger/code-context.md)   
 [シンボルのプロバイダー](../../extensibility/debugger/symbol-provider.md)   
 [シンボルのプロバイダー インターフェイス](../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [デバッガー コンテキスト](../../extensibility/debugger/debugger-contexts.md)
