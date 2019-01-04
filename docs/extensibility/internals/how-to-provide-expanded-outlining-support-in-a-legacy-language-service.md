---
title: アウトラインの言語サービスでサポートを提供 |Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: a26d9dbc67f502e30968f3db89834b12e02ae3e5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53965552"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>方法: 従来の言語サービスでのアウトラインの拡張のサポートを提供します。
お使いの言語をサポートしている以外のアウトラインのサポートを拡張するための 2 つのオプションがある、**定義に折りたたむ**コマンド。 エディター コントロールのアウトライン領域を追加し、クライアント制御のアウトライン領域を追加できます。  
  
## <a name="adding-editor-controlled-outline-regions"></a>エディター コントロールのアウトライン領域を追加します。  
 折りたたまれている場合にアウトライン領域を作成して、領域を展開すると、かどうかを処理するために、エディターをこのアプローチを使用してなど。 アウトラインのサポートを提供する 2 つのオプションは、このオプションは堅牢な少なくします。 このオプションで指定されたスパンを使用してテキストの上新しいアウトライン領域を作成する<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>します。 このリージョンが作成された後、その動作は、エディターによって制御されます。 次の手順を使用すると、エディター コントロールのアウトライン領域を実装します。  
  
### <a name="to-implement-an-editor-controlled-outline-region"></a>エディター コントロールのアウトライン領域を実装するには  
  
1.  呼び出す`QueryService`の <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>  
  
     ポインターが返されます<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>します。  
  
2.  呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>テキストを指定したバッファーのポインターに渡します。 ポインターが返されます、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>バッファーのオブジェクト。  
  
3.  呼び出す<xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>で<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>へのポインターの<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>します。  
  
4.  呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>を追加したり、時に新しいリージョンを説明します。  
  
     このメソッドでは、アウトライン、既存のアウトライン領域を削除または保持するかどうか、アウトライン領域を展開するか既定で折りたたまれているかどうかにテキストの範囲を指定できます。  
  
## <a name="add-client-controlled-outline-regions"></a>クライアント管理のアウトライン領域を追加します。  
 使用するなどのクライアント管理 (スマート) の実装のアウトライン表示するには、このアプローチを使用して、[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]と[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]言語サービス。 古いアウトライン領域を無効になったときに破棄するには、必要に応じて新しいアウトライン領域を作成する、独自のアウトライン表示を管理する言語サービスは、テキスト バッファーの内容を監視します。  
  
### <a name="to-implement-a-client-controlled-outline-region"></a>クライアント管理のアウトライン領域を実装するには  
  
1.  呼び出す`QueryService`の<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>します。 ポインターが返されます<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>します。  
  
2.  呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>テキストを指定したバッファーのポインターに渡します。 これは、バッファーの非表示のテキストのセッションを既にが存在するかどうかを示します。  
  
3.  かどうかには、テキストのセッションが既に存在し、いずれか、および既存へのポインターを作成する必要はありません<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>オブジェクトが返されます。 このポインターを使用して、列挙し、アウトライン領域を作成します。 それ以外の場合、呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>バッファーの非表示のテキストのセッションを作成します。 ポインター、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>オブジェクトが返されます。  
  
    > [!NOTE]
    >  呼び出すと<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>、非表示のテキストのクライアントを指定できます (つまり、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>オブジェクト)。 このクライアントに通知するときに非表示のテキストまたはアウトライン領域を展開するか、ユーザーが折りたたまれています。  
  
4.  呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>構造) パラメーター。値を指定<xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE>で、`iType`のメンバー、<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>構造体を非表示の領域ではなく、アウトライン領域を作成することを示します。 クライアントが管理またはでエディター制御領域は、かどうかを指定、`dwBehavior`のメンバー、<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>構造体。 スマート アウトライン実装は、さまざまなエディターとクライアントの制御にアウトライン領域を含めることができます。 アウトライン領域が折りたたまれて、「…」などのときに表示されるバナー テキストを指定、`pszBanner`のメンバー、<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>構造体。 エディターの既定のバナー テキストを非表示の領域は、「...」です。