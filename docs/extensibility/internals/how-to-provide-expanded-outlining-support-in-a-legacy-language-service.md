---
title: "言語サービスでのサポートをアウトライン表示を提供します |。Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
caps.latest.revision: 16
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
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: fc502e4430a49284cffe14386249999d82085f1c
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>方法: レガシ言語サービスでの展開のアウトライン サポートを提供
使用する言語をサポートする以外のアウトラインのサポートを拡張するための&2; つのオプションがある、**定義に縮小**コマンドです。 エディター コントロールのアウトライン領域を追加し、クライアント制御のアウトライン領域を追加できます。  
  
## <a name="adding-editor-controlled-outline-regions"></a>エディター コントロールのアウトライン領域を追加します。  
 折りたたまれているアウトライン領域を作成し、領域が展開されているかどうかを処理するエディターを使用し、この方法を使用してなどです。 アウトラインのサポートを提供する&2; つのオプションは、このオプションは、少なくとも堅牢です。 このオプションで<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>を使用してテキストの指定した範囲に新しいアウトライン領域を作成します。 この領域を作成した後、その動作は、エディターによって制御されます。 次の手順を使用すると、エディター コントロールのアウトライン領域を実装します。  
  
#### <a name="to-implement-an-editor-controlled-outline-region"></a>エディター コントロールのアウトライン領域を実装するには  
  
1.  呼び出す`QueryService`の<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager></xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>へのポインターを返します  
  
2.  呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>を渡すことで指定されたテキスト バッファーのポインター</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> 。 ポインターが返されます、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>バッファーのオブジェクト</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>。  
  
3.  <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>へのポインターの</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>上</xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>を呼び出す  
  
4.  呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>を追加したりより新しい一度に領域の概要を説明します</xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>。  
  
     このメソッドでは、アウトライン、既存のアウトライン領域を削除または、保持するかどうか、アウトライン領域を広げる場合または既定で折りたたまれているかどうかをテキストの範囲を指定することができます。  
  
## <a name="adding-client-controlled-outline-regions"></a>クライアント管理されているアウトライン領域を追加します。  
 アウトラインのクライアント管理の対象 (スマート) を実装するには、この方法では、使用すると同様に使用する、[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]と[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]言語サービスです。 独自のアウトライン表示を管理する言語サービスは、それらが無効になったときに古いアウトライン領域を破棄するために、必要に応じて新しいアウトライン領域を作成する、テキスト バッファーの内容を監視します。  
  
#### <a name="to-implement-a-client-controlled-outline-region"></a>クライアント管理されているアウトライン領域を実装するには  
  
1.  呼び出す`QueryService` <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager></xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> 。 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>へのポインターを返します  
  
2.  呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>を渡すことで指定されたテキスト バッファーのポインター</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> 。 これは、バッファーの非表示のテキストのセッションを既にが存在するかどうかを決定します。  
  
3.  テキスト セッションは既に存在するかどうかは、1 つ、および既存へのポインターを作成する必要はありません<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>オブジェクトが返されます</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>。 このポインターを使用して、列挙し、アウトライン領域を作成します。 それ以外の場合、呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>バッファーの非表示のテキストのセッションを作成します</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>。 ポインター、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>オブジェクトが返されます</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>。  
  
    > [!NOTE]
    >  呼び出すと<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>、非表示のテキストのクライアントを指定できます (つまり、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>オブジェクト).</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> このクライアントに通知するときに非表示のテキストまたはアウトライン領域を展開するか、ユーザーが折りたたまれています。  
  
4.  呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>構造) パラメーター: の値を指定して<xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE>で、`iType`のメンバー、<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>構造を非表示の領域ではなく、アウトライン領域を作成することを示します</xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion></xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE></xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>。 リージョンがクライアント コントロールまたはエディター管理対象で配置するかどうかを指定、`dwBehavior`のメンバー、<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>構造体</xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>。 スマートなアウトライン ニーズは、さまざまなエディターとクライアント制御のアウトライン領域を含めることができます。 アウトライン領域は折りたたまれ、「...」などのときに表示されるバナー テキストを指定する、`pszBanner`のメンバー、<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>構造体</xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>。 エディターの既定のバナー テキストを非表示の領域は、「...」です。
