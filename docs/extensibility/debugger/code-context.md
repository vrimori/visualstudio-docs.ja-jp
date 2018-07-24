---
title: コード コンテキスト |Microsoft Docs
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
ms.openlocfilehash: 31b1f3d91fd44308c1737f8066c13af730454abe
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2018
ms.locfileid: "39203346"
---
# <a name="code-context"></a>コード コンテキスト
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 、デバッグ、**コード コンテキスト**:  
  
-   デバッグ エンジン (DE) に既知としては、コード内の位置の抽象化を提供します。 ほとんどのランタイム アーキテクチャの今日では、コードのコンテキストできます見なすことがプログラムの命令ストリーム内のアドレス。 従来とは異なる言語では、コードは、命令表現いない可能性があります、その他のいくつかの方法でコードのコンテキストを表すことができます。  
  
-   デバッグ中のプログラムの実行のストリームの現在の位置をについて説明します。  
  
-   ブレークポイントにプログラムが停止時にのみ存在します。  
  
-   関連付けられているドキュメント コンテキストがあります。  
  
-   によって実装される、 [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md)インターフェイス。  
  
## <a name="see-also"></a>関連項目  
 [ドキュメントのコンテキスト](../../extensibility/debugger/document-context.md)   
 [デバッガー コンテキスト](../../extensibility/debugger/debugger-contexts.md)