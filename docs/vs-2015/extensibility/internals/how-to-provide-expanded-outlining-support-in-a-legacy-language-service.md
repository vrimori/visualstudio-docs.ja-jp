---
title: '方法: 従来の言語サービスでのアウトラインの拡張のサポートを提供 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a6371339da12d88832e84d5086ed2d8a83226a94
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49239541"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>方法: 従来の言語サービスでのアウトラインの拡張のサポートを提供します。
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

お使いの言語をサポートしている以外のアウトラインのサポートを拡張するための 2 つのオプションがある、**定義に折りたたむ**コマンド。 エディター コントロールのアウトライン領域を追加し、クライアント制御のアウトライン領域を追加できます。  
  
## <a name="adding-editor-controlled-outline-regions"></a>エディター コントロールのアウトライン領域を追加します。  
 折りたたまれている場合にアウトライン領域を作成して、領域を展開すると、かどうかを処理するために、エディターをこのアプローチを使用してなど。 アウトラインのサポートを提供する 2 つのオプションは、このオプションは堅牢な少なくします。 このオプションで指定されたスパンを使用してテキストの上新しいアウトライン領域を作成する<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>します。 このリージョンが作成された後、その動作は、エディターによって制御されます。 次の手順を使用すると、エディター コントロールのアウトライン領域を実装します。  
  
#### <a name="to-implement-an-editor-controlled-outline-region"></a>エディター コントロールのアウトライン領域を実装するには  
  
1.  呼び出す`QueryService`の <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>  
  
     ポインターが返されます<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>します。  
  
2.  呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>テキストを指定したバッファーのポインターに渡します。 ポインターが返されます、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>バッファーのオブジェクト。  
  
3.  呼び出す<xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>で<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>へのポインターの<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>します。  
  
4.  呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>を追加したり、時に新しいリージョンを説明します。  
  
     このメソッドでは、アウトライン、既存のアウトライン領域を削除または保持するかどうか、アウトライン領域を展開するか既定で折りたたまれているかどうかにテキストの範囲を指定できます。  
  
## <a name="adding-client-controlled-outline-regions"></a>クライアント管理のアウトライン領域を追加します。  
 使用するなどのクライアント管理 (スマート) の実装のアウトライン表示するには、このアプローチを使用して、[!INCLUDE[csprcs](../../includes/csprcs-md.md)]と[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]言語サービス。 独自のアウトライン表示を管理する言語サービスは、必要に応じて新しいアウトライン領域を作成して、無効になったときに古いアウトライン領域を破棄するには、テキスト バッファーの内容を監視します。  
  
#### <a name="to-implement-a-client-controlled-outline-region"></a>クライアント管理のアウトライン領域を実装するには  
  
1.  呼び出す`QueryService`の<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>します。 ポインターが返されます<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>します。  
  
2.  呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>テキストを指定したバッファーのポインターに渡します。 これは、バッファーの非表示のテキストのセッションを既にが存在するかどうかを示します。  
  
3.  かどうかには、テキストのセッションが既に存在し、いずれか、および既存へのポインターを作成する必要はありません<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>オブジェクトが返されます。 このポインターを使用して、列挙し、アウトライン領域を作成します。 それ以外の場合、呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>バッファーの非表示のテキストのセッションを作成します。 ポインター、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>オブジェクトが返されます。  
  
    > [!NOTE]
    >  呼び出すと<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>、非表示のテキストのクライアントを指定できます (つまり、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>オブジェクト)。 このクライアントに通知するときに非表示のテキストまたはアウトライン領域を展開するか、ユーザーが折りたたまれています。  
  
4.  呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>構造) パラメーター: の値を指定<xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE>で、`iType`のメンバー、<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>構造体を非表示の領域ではなく、アウトライン領域を作成することを示します。 クライアントが管理またはでエディター制御領域は、かどうかを指定、`dwBehavior`のメンバー、<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>構造体。 スマート アウトライン実装は、さまざまなエディターとクライアントの制御にアウトライン領域を含めることができます。 アウトライン領域が折りたたまれて、「…」などのときに表示されるバナー テキストを指定、`pszBanner`のメンバー、<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>構造体。 エディターの既定のバナー テキストを非表示の領域は、「...」です。

