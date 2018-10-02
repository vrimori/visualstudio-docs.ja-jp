---
title: コード コンテキスト |Microsoft Docs
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
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4e9ff125a75731de5ca312e5417996f9c6dda764
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47545172"
---
# <a name="code-context"></a>コード コンテキスト
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[コード コンテキスト](https://docs.microsoft.com/visualstudio/extensibility/debugger/code-context)します。  
  
[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 、デバッグ、**コード コンテキスト**:  
  
-   デバッグ エンジン (DE) に既知としては、コード内の位置の抽象化を提供します。 ほとんどのランタイム アーキテクチャの今日では、コードのコンテキストできます見なすことがプログラムの命令ストリーム内のアドレス。 従来とは異なる言語では、コードは、命令表現いない可能性があります、その他のいくつかの方法でコードのコンテキストを表すことができます。  
  
-   デバッグ中のプログラムの実行のストリームの現在の位置をについて説明します。  
  
-   ブレークポイントにプログラムが停止時にのみ存在します。  
  
-   関連付けられているドキュメント コンテキストがあります。  
  
-   によって実装される、 [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md)インターフェイス。  
  
## <a name="see-also"></a>関連項目  
 [ドキュメントのコンテキスト](../../extensibility/debugger/document-context.md)   
 [デバッガー コンテキスト](../../extensibility/debugger/debugger-contexts.md)

