---
title: "コンテキストのコード |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 97a4c8f8a9a710fab70760d9cb6eabb61de7a26f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="code-context"></a>コード コンテキスト
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 、デバッグ、**コード コンテキスト**:  
  
-   認識されているため、デバッグ エンジン (DE) は、コード内の位置の抽象化を提供します。 ほとんどのランタイム アーキテクチャ今日では、コードのコンテキストできますと見なすプログラムの命令ストリーム内のアドレス。 従来とは異なる言語では、ここで、命令コードを表すことができましていない、他のいくつかの方法でコードのコンテキストを表すことができます。  
  
-   デバッグ中のプログラムの実行ストリーム内の現在位置をについて説明します。  
  
-   ブレークポイントの位置にプログラムが停止時にのみ存在します。  
  
-   関連付けられているドキュメントのコンテキストがあります。  
  
-   によって実装される、 [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md)インターフェイスです。  
  
## <a name="see-also"></a>参照  
 [ドキュメントのコンテキスト](../../extensibility/debugger/document-context.md)   
 [デバッガー コンテキスト](../../extensibility/debugger/debugger-contexts.md)