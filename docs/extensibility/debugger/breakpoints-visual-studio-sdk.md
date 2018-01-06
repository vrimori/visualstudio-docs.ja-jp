---
title: "ブレークポイント (Visual Studio SDK) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: be8f0b36ebe57041e9d36b8f606bd5bddd0601bd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="breakpoints-visual-studio-sdk"></a>ブレークポイント (Visual Studio SDK)
ブレークポイントの 3 種類があります。 保留中の、バインド、およびエラーです。  
  
 **保留中のブレークポイント A:**  
  
-   1 つまたは複数のプログラム内の 1 つまたは複数のコード コンテキストにブレークポイントをバインドするために必要なすべての情報を含む抽象です。 たびに、原因を読み込むコードをデバッグ対象のプログラム デバッグ エンジン チェックすべて保留中のブレークポイントで連結することができますを参照してください。  
  
     自体保留中のブレークポイントことはありません、コードにバインドしますが、ではなく収集し、言います生成されたすべてのバインドされたブレークポイントを含むです。  
  
-   によって表される、 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)インターフェイスです。  
  
 **バインドされたブレークポイント:**  
  
-   ブレークポイントの抽象化に関連付けられているか、1 つのコードのコンテキストにバインドされています。 バインドされた各ブレークポイントは、保留中のブレークポイントに応答が生成されます。 保留中のブレークポイントでは、バインドされた 2 つ以上のブレークポイントを生成できます、ただし。  
  
     コードが読み込まれると、バインドされたブレークポイントはバインドされていないし、破棄されます。  
  
-   によって表される、 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)インターフェイスです。  
  
 **エラー ブレークポイントの場合:**  
  
-   抽象コード コンテキストに保留中のブレークポイントをバインドするときにエラーを記述するためです。 エラー ブレークポイントでは、場所や、ブレークポイント式自体、どちらのエラーについて説明します。 詳細については、次を参照してください。[ブレークポイントのバインディング](../../extensibility/debugger/binding-breakpoints.md)です。  
  
     ブレークポイントのエラー、エラーまたは警告を使用できます。  
  
-   によって表される、 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)インターフェイスです。  
  
## <a name="see-also"></a>参照  
 [プログラム](../../extensibility/debugger/programs.md)   
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)   
 [コード コンテキスト](../../extensibility/debugger/code-context.md)   
 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)