---
title: アウトラインの言語サービスでのサポートを提供 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6467a1e3386daedc4a67aa420c06cf01187b8d22
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>方法: レガシ言語サービスでの展開のアウトライン サポートを提供
使用する言語をサポートする以外のアウトラインのサポートを拡張するための 2 つのオプションがある、**定義に縮小**コマンド。 エディター コントロールのアウトライン領域を追加し、クライアント管理されているアウトライン領域を追加できます。  
  
## <a name="adding-editor-controlled-outline-regions"></a>エディター コントロールのアウトライン領域を追加します。  
 折りたたまれている場合、アウトライン領域を作成し、エディターで、領域が展開されているかどうかの処理を許可するこの方法を使用してなど。 アウトラインのサポートを提供する 2 つのオプションのこのオプションは、少なくとも堅牢です。 このオプションのテキストを使用する指定されたスパン経由で新しいアウトライン領域を作成する<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>です。 この領域を作成した後、その動作は、エディターによって制御されます。 次の手順を使用すると、エディター コントロールのアウトライン領域を実装します。  
  
#### <a name="to-implement-an-editor-controlled-outline-region"></a>エディター コントロールのアウトライン領域を実装するには  
  
1.  呼び出す`QueryService`の <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>  
  
     ポインターが返されます。<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>です。  
  
2.  呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>テキストを指定したバッファーのポインターに渡します。 ポインターが返されます、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>バッファーのオブジェクト。  
  
3.  呼び出す<xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>で<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>へのポインターの<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>します。  
  
4.  呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>を追加したりより新しい、一度に領域を説明します。  
  
     このメソッドでは、アウトライン、既存のアウトライン領域を削除または、保持するかどうか、アウトライン領域が展開または既定で折りたたまれているかどうかをテキストの範囲を指定することができます。  
  
## <a name="adding-client-controlled-outline-regions"></a>クライアント管理されているアウトライン領域を追加します。  
 によって使用されるアウトラインのクライアント管理の対象 (スマート) を実装するには、この方法などを使用して、[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]と[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]言語サービス。 独自のアウトライン表示を管理する言語サービスは、無効になったときに古いアウトライン領域を破棄するために、必要に応じて新しいアウトライン領域を作成するテキスト バッファーの内容を監視します。  
  
#### <a name="to-implement-a-client-controlled-outline-region"></a>クライアント管理されているアウトライン領域を実装するには  
  
1.  呼び出す`QueryService`の<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>します。 ポインターが返されます。<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>です。  
  
2.  呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>テキストを指定したバッファーのポインターに渡します。 これは、バッファーのテキストの非表示セッションを既にが存在するかどうかを判断します。  
  
3.  テキスト セッションは既に存在するかどうかは、1 つ、および既存へのポインターを作成する必要はありません<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>オブジェクトが返されます。 列挙し、アウトライン領域を作成するには、このポインターを使用します。 それ以外の場合、呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>バッファーのテキストの非表示セッションを作成します。 ポインター、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>オブジェクトが返されます。  
  
    > [!NOTE]
    >  呼び出すと<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>、非表示テキストのクライアントを指定できます (つまり、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>オブジェクト)。 このクライアントに通知するときに非表示テキストまたはにアウトライン領域を展開するか、ユーザーが折りたたまれています。  
  
4.  呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>構造体) パラメーター: の値を指定して<xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE>で、`iType`のメンバー、<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>構造を非表示の領域ではなく、アウトライン領域を作成することを示します。 地域がクライアント制御またはでエディター制御するかどうかを指定、`dwBehavior`のメンバー、<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>構造体。 スマート アウトライン実装では、さまざまなエディターとクライアントの制御にアウトライン領域を含めることができます。 アウトライン領域が折りたたまれている、「...」などのときに表示されるバナー テキストを指定、`pszBanner`のメンバー、<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>構造体。 エディターの既定のバナー テキストを非表示の領域は、「...」です。