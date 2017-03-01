---
title: "ブレークポイント (Visual Studio SDK) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
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
ms.openlocfilehash: fd0eccfa45f20217291b2e00eb175f8eac49d42d
ms.lasthandoff: 02/22/2017

---
# <a name="breakpoints-visual-studio-sdk"></a>ブレークポイント (Visual Studio SDK)
ブレークポイントの&3; つの種類があります: 保留中、バインド、およびエラーです。  
  
 **保留中のブレークポイント A:**  
  
-   1 つまたは複数のプログラム内の&1; つまたは複数のコード コンテキストにブレークポイントをバインドするために必要なすべての情報を含む抽象化です。 たびに、原因を読み込むコードをデバッグ対象のプログラム デバッグ エンジンは、確認すべて保留中のブレークポイントで連結することができますを参照してください。  
  
     自体保留中のブレークポイントことはありません、コードにバインドではなく収集し、言いますこれによって生成されるすべてのバインドされているブレークポイントが含まれています。  
  
-   によって表される、 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)インターフェイスです。  
  
 **バインドされたブレークポイント。**  
  
-   ブレークポイントの抽象化に関連付けられているか、1 つのコードのコンテキストにバインドします。 バインドされた各ブレークポイントは、保留中のブレークポイントに応答が生成されます。 保留中のブレークポイントでは、バインドされた&2; つ以上のブレークポイントただし、生成、ことができます。  
  
     コードが読み込まれると、バインドされたブレークポイントはバインドされていないし、破棄されます。  
  
-   によって表される、 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)インターフェイスです。  
  
 **エラー ブレークポイントの場合:**  
  
-   コードのコンテキストに保留中のブレークポイントをバインドするときにエラーを記述するための抽象化です。 エラー ブレークポイントでは、場所か、ブレークポイント式自体のいずれかのエラーについて説明します。 詳細については、次を参照してください。[バインド ブレークポイント](../../extensibility/debugger/binding-breakpoints.md)します。  
  
     ブレークポイント エラー、エラーまたは警告を使用できます。  
  
-   によって表される、 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)インターフェイスです。  
  
## <a name="see-also"></a>関連項目  
 [プログラム](../../extensibility/debugger/programs.md)   
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)   
 [コードのコンテキスト](../../extensibility/debugger/code-context.md)   
 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
