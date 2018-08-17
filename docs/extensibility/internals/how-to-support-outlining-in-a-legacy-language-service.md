---
title: '方法: 従来の言語サービスでのアウトラインのサポート |Microsoft Docs'
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
ms.openlocfilehash: b6f9ba947aee0276e2cca6270438cdaf20e7626e
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510958"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>方法: 従来の言語サービスでのアウトラインのサポート
アウトライン表示は、展開または折りたたむテキストの異なるリージョンに使用されます。 使用方法のアウトラインはさまざまな言語によって別々 に定義できます。 詳細については、「[アウトライン](../../ide/outlining.md)」を参照してください。  
  
 従来の言語サービスは、VSPackage の一部として実装されますが、言語サービスの機能を実装する新しい方法は MEF 拡張機能を使用します。 アウトライン表示を実装する新しい方法の詳細についてを参照してください。[チュートリアル: アウトライン](../../extensibility/walkthrough-outlining.md)します。  
  
> [!NOTE]
>  新しいエディターの API をできるだけ早く使用を開始することをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用することができます。  
  
 言語サービスのこのコマンドをサポートする方法を次に示します。  
  
## <a name="to-support-outlining"></a>アウトライン表示をサポートするには  
  
1.  実装<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage>言語サービス オブジェクト。  
  
2.  呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>新しいアウトライン領域を追加する現在のアウトライン セッション オブジェクトにします。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 ユーザーが選択すると**定義に縮小**上、**アウトライン**メニューで、IDE の呼び出し<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A>言語サービス。  
  
 このメソッドが呼び出されるに IDE が渡されます。、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> (テキスト バッファーへのポインター) と<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>(現在のアウトラインのセッションへのポインター)。  
  
 呼び出すことができます、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>メソッドでこれらのリージョンを指定することで、複数のアウトライン領域に対する、`rgOutlnReg`パラメーター。 `rgOutlnReg`パラメーターは、<xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion>構造体。 このプロセスでは、非表示の領域の特定の地域の展開または折りたたまれているかどうかなどのさまざまな特性を指定することができます。  
  
> [!NOTE]
>  改行文字を非表示について注意が必要です。 非表示のテキストを拡張する最初の行の先頭から最後のまま新しい行の最後の文字を表示、セクションの最後の行の文字。  
  
## <a name="see-also"></a>関連項目  
 [方法: 非表示のテキストを提供する従来の言語サービスでのサポート](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)   
 [方法: 従来の言語サービスでのアウトラインの拡張のサポートを提供します。](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)