---
title: コンテキストのコード |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9a84596246ae930cdffc0265f2f2e09652661819
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="code-context"></a>コード コンテキスト
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 、デバッグ、**コード コンテキスト**:  
  
-   認識されているため、デバッグ エンジン (DE) は、コード内の位置の抽象化を提供します。 ほとんどのランタイム アーキテクチャ今日では、コードのコンテキストできますと見なすプログラムの命令ストリーム内のアドレス。 従来とは異なる言語では、ここで、命令コードを表すことができましていない、他のいくつかの方法でコードのコンテキストを表すことができます。  
  
-   デバッグ中のプログラムの実行ストリーム内の現在位置をについて説明します。  
  
-   ブレークポイントの位置にプログラムが停止時にのみ存在します。  
  
-   関連付けられているドキュメントのコンテキストがあります。  
  
-   によって実装される、 [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md)インターフェイスです。  
  
## <a name="see-also"></a>関連項目  
 [ドキュメントのコンテキスト](../../extensibility/debugger/document-context.md)   
 [デバッガー コンテキスト](../../extensibility/debugger/debugger-contexts.md)