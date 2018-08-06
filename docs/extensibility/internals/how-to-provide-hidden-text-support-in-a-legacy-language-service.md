---
title: '方法: 従来の言語サービスでの非表示のテキストのサポートを提供 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d368caaa9b65f6f9ab8b12c1f49994e3bfe16670
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39511961"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>方法: 非表示のテキストを提供する従来の言語サービスでのサポート
アウトライン領域以外にも非表示のテキスト領域を作成できます。 非表示のテキスト領域は、クライアントが管理またはエディター コントロールとテキストの特定の領域を完全に非表示に使用されます。 エディターには、水平線として非表示の領域が表示されます。 この例は、**スクリプトのみ**HTML エディターで表示します。  
  
  
## <a name="to-implement-a-hidden-text-region"></a>非表示のテキスト領域を実装するには  
  
1.  呼び出す`QueryService`の<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>します。  
  
     ポインターが返されます<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>します。  
  
2.  呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>テキストを指定したバッファーのポインターに渡します。 これは、バッファーの非表示のテキストのセッションを既にが存在するかどうかを示します。  
  
3.  既に存在するかどうかは、1 つと、既存のポインターを作成する必要はありません<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>オブジェクトが返されます。 このポインターを使用して、列挙し、非表示のテキスト領域を作成します。 それ以外の場合、呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>バッファーの非表示のテキストのセッションを作成します。  
  
     ポインター、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>オブジェクトが返されます。  
  
    > [!NOTE]
    >  呼び出すと`CreateHiddenTextSession`、非表示のテキストのクライアントを指定できます (つまり、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>)。 非表示のテキストのクライアントには、非表示のテキストまたはアウトラインが展開されたか、ユーザーが折りたたまれているときに通知します。  
  
4.  呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>を追加したりより新しいアウトライン領域を時では、次の情報を指定する、 `reHidReg` (<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>) パラメーター。  
  
    1.  値を指定`hrtConcealed`で、`iType`のメンバー、<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>構造体をアウトライン領域ではなく、非表示の領域を作成することを示します。  
  
        > [!NOTE]
        >  非表示の領域は表示されず、エディターに自動的にその存在は示すを非表示の領域の周りの線が表示されます。  
  
    2.  クライアントが管理またはでエディター制御領域は、かどうかを指定、`dwBehavior`のメンバー、<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>構造体。 スマート アウトライン実装は、さまざまなアウトラインのエディターとクライアントの制御、および非表示のテキスト領域を含めることができます。