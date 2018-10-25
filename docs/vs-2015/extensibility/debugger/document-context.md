---
title: コンテキストのドキュメント |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5e1bbe5ac2f2c752fcf6f0b5a0b0b95be144ac8f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49237433"
---
# <a name="document-context"></a>ドキュメント コンテキスト
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 、デバッグ、**ドキュメント コンテキスト**:  
  
-   ソース ファイル内の位置を表します。 ソース ファイルが存在していない可能性がある言語では、ドキュメントのコンテキストは、通常、実行時環境で生成されるドキュメント内の位置を識別します。 たとえば、スクリプト エンジンでは、スクリプトからドキュメントを生成する可能性があります。 詳細については、次を参照してください。[ドキュメントの位置](../../extensibility/debugger/document-position.md)します。  
  
-   コードのコンテキストに対応するソース ドキュメント内の位置をについて説明します。 シンボルのハンドラーは、コードのコンテキストをコンパイラまたはインタープリターによって生成される情報を使用して、ドキュメントのコンテキストにマップします。  
  
-   によって実装される、 [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md)インターフェイス。  
  
## <a name="see-also"></a>関連項目  
 [コード コンテキスト](../../extensibility/debugger/code-context.md)   
 [シンボル プロバイダー](../../extensibility/debugger/symbol-provider.md)   
 [シンボルプロバイダーのインターフェイス](../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [デバッガー コンテキスト](../../extensibility/debugger/debugger-contexts.md)

