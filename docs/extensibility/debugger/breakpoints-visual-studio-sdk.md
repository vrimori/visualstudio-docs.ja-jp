---
title: ブレークポイント (Visual Studio SDK) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 146c8c7e17017a675ad1077d03800328b0d345d3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49932677"
---
# <a name="breakpoints-visual-studio-sdk"></a>ブレークポイント (Visual Studio SDK)
ブレークポイントの 3 種類があります。 保留中、バインド、およびエラー。  
  
 **保留中のブレークポイント A:**  
  
- 1 つまたは複数のプログラム内の 1 つまたは複数のコード コンテキストにブレークポイントをバインドするために必要なすべての情報を格納する抽象化。 毎回、原因を読み込むコードをデバッグ対象のプログラム デバッグ エンジンを確認します保留中のすべてのブレークポイントをバインドできるかどうかを参照してください。  
  
   自体保留中のブレークポイントことはありませんコードにバインドしますではなく収集し、言いますを生成するすべてのバインドされたブレークポイントを含みます。  
  
- によって表される、 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)インターフェイス。  
  
  **バインドされたブレークポイント。**  
  
- ブレークポイントの抽象化に関連付けられているか 1 つのコード コンテキストに制限されます。 バインドされた各ブレークポイントは保留中のブレークポイントへの応答で生成されます。 ただし、保留中のブレークポイントは、複数のバインドされたブレークポイントが生成ことができます。  
  
   コードが読み込まれると、バインドされたブレークポイントはバインドされていないし、破棄されます。  
  
- によって表される、 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)インターフェイス。  
  
  **エラー ブレークポイントの場合:**  
  
- コードのコンテキストに保留中のブレークポイントをバインドするときにエラーを説明するための抽象型です。 エラー、ブレークポイントでは、またはブレークポイント式自体の場所で、いずれかのエラーについて説明します。 詳細については、次を参照してください。[ブレークポイントのバインディング](../../extensibility/debugger/binding-breakpoints.md)します。  
  
   ブレークポイントのエラーは、エラーまたは警告のいずれかにできます。  
  
- によって表される、 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)インターフェイス。  
  
## <a name="see-also"></a>関連項目  
 [プログラム](../../extensibility/debugger/programs.md)   
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)   
 [コード コンテキスト](../../extensibility/debugger/code-context.md)   
 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)