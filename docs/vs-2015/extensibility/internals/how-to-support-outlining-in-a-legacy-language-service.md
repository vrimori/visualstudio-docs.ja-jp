---
title: '方法: 従来の言語サービスでのアウトラインのサポート |Microsoft Docs'
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
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 336e8c04116afa5523a10f7e0617fdc18678c5d7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539881"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>方法: 従来の言語サービスでのアウトラインのサポート
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: 従来の言語サービスでのサポートのアウトライン](https://docs.microsoft.com/visualstudio/extensibility/internals/how-to-support-outlining-in-a-legacy-language-service)します。  
  
アウトライン表示は、展開または折りたたむテキストの異なるリージョンに使用されます。 使用方法のアウトラインはさまざまな言語によって別々 に定義できます。 詳細については、「[アウトライン](../../ide/outlining.md)」を参照してください。  
  
 従来の言語サービスは、VSPackage の一部として実装されますが、言語サービスの機能を実装する新しい方法は MEF 拡張機能を使用します。 アウトライン表示を実装する新しい方法の詳細についてを参照してください。[チュートリアル: アウトライン](../../extensibility/walkthrough-outlining.md)します。  
  
> [!NOTE]
>  新しいエディターの API をできるだけ早く使用を開始することをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用することができます。  
  
 言語サービスのこのコマンドをサポートする方法を次に示します。  
  
### <a name="to-support-outlining"></a>アウトライン表示をサポートするには  
  
1.  実装<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage>言語サービス オブジェクト。  
  
2.  呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>新しいアウトライン領域を追加する現在のアウトライン セッション オブジェクトにします。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 ユーザーが選択すると**定義に縮小**上、**アウトライン**メニューで、IDE の呼び出し<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A>言語サービス。  
  
 このメソッドが呼び出されるに IDE が渡されます。、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> (テキスト バッファーへのポインター) と<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>(現在のアウトラインのセッションへのポインター)。  
  
 呼び出すことができます、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>メソッドでこれらのリージョンを指定することで、複数のアウトライン領域に対する、`rgOutlnReg`パラメーター。 `rgOutlnReg`パラメーターは、<xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion>構造体。 このプロセスでは、非表示の領域の特定の地域の展開または折りたたまれているかどうかなどのさまざまな特性を指定できます。  
  
> [!NOTE]
>  改行文字を非表示について注意が必要です。 非表示のテキストを拡張する最初の行の先頭から最後のまま新しい行の最後の文字を表示、セクションの最後の行の文字。  
  
## <a name="see-also"></a>関連項目  
 [方法: 従来の言語サービスでの非表示のテキストのサポートを提供します。](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)   
 [方法: 従来の言語サービスでのアウトラインの拡張サポートの提供](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

