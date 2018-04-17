---
title: '方法: レガシ言語サービスでのアウトラインがサポート |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f9880c5c255118478d15f34f9a9245a1c25d97fd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>方法: レガシ言語サービスのアウトライン表示をサポート
アウトライン表示は、展開または折りたたみのテキストのさまざまな地域に使用されます。 アウトライン方法が使用されるさまざまな言語で定義が異なることができます。 詳細については、「[アウトライン](../../ide/outlining.md)」を参照してください。  
  
 レガシ言語サービスは、VSPackage の一部として実装されますが、MEF 拡張機能を使用する言語サービスの機能を実装する新しい方法です。 アウトライン表示を実装する新しい方法の詳細についてを参照してください[チュートリアル: アウトライン](../../extensibility/walkthrough-outlining.md)です。  
  
> [!NOTE]
>  エディターを使用して、新しい API できるだけ早く開始することをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用できます。  
  
 言語サービスに対してこのコマンドをサポートする方法を次に示します。  
  
### <a name="to-support-outlining"></a>アウトライン表示をサポートするには  
  
1.  実装<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage>言語サービス オブジェクトにします。  
  
2.  呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>現在のアウトライン セッション オブジェクトを新規にアウトライン領域を追加します。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 ユーザーが選択すると**定義に縮小**上、**アウトライン**] メニューの [IDE 呼び出し<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A>言語サービスでします。  
  
 このメソッドが呼び出されると、IDE 渡します、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>ポインター (テキスト バッファーへのポインター) と<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>(現在のアウトライン セッションへのポインター)。  
  
 呼び出すことができます、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>メソッドでこれらの領域を指定することによって複数のアウトライン領域を`rgOutlnReg`パラメーター。 `rgOutlnReg`パラメーターは、<xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion>構造体。 このプロセスでは、特定の地域の展開または折りたたむかどうかなど、非表示領域のさまざまな特性を指定できます。  
  
> [!NOTE]
>  改行文字を非表示の注意します。 非表示テキスト拡張することは、最初の行の先頭から最後のれ、新しい行の最後の文字を表示、セクションの最後の行の文字です。  
  
## <a name="see-also"></a>関連項目  
 [方法: レガシ言語サービスでの非表示テキストのサポートを提供](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)   
 [方法: 従来の言語サービスでのアウトラインの拡張サポートの提供](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)