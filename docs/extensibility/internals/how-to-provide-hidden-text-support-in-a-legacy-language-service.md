---
title: "方法: レガシ言語サービスでの非表示テキストのサポートを提供 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f7aab5978d2fc5f7bee82b097ed61a9603d7e198
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>方法: レガシ言語サービスでの非表示テキストのサポートを提供
アウトライン領域以外にも非表示のテキスト領域を作成できます。 非表示テキスト領域は、クライアント管理の対象またはエディター コントロールとテキストの範囲を完全に非表示に使用します。 エディターには、水平の線としての非表示の領域が表示されます。 この例は、HTML エディターのスクリプトのみのビューです。  
  
## <a name="procedure"></a>プロシージャ  
  
#### <a name="to-implement-a-hidden-text-region"></a>非表示のテキスト領域を実装するには  
  
1.  呼び出す`QueryService`の<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>します。  
  
     ポインターが返されます。<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>です。  
  
2.  呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>テキストを指定したバッファーのポインターに渡します。 これは、バッファーのテキストの非表示セッションを既にが存在するかどうかを判断します。  
  
3.  いずれかが既に存在するかどうかは、いずれかと、既存のポインターを作成する必要はありません<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>オブジェクトが返されます。 列挙し、非表示のテキスト領域を作成するには、このポインターを使用します。 それ以外の場合、呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>バッファーのテキストの非表示セッションを作成します。  
  
     ポインター、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>オブジェクトが返されます。  
  
    > [!NOTE]
    >  呼び出すと`CreateHiddenTextSession`、非表示テキストのクライアントを指定できます (つまり、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>)。 非表示テキスト クライアントは、非表示テキストまたはアウトライン表示が展開されたり、ユーザーが折りたたまれている場合に通知します。  
  
4.  呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>を追加したりより新しいアウトライン領域、一度にで次の情報を指定する、 `reHidReg` (<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>) パラメーター。  
  
    1.  値を指定して`hrtConcealed`で、`iType`のメンバー、<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>アウトライン領域ではなく、非表示の領域を作成することを示すために構造体。  
  
        > [!NOTE]
        >  非表示領域は表示されず、エディターに自動的にその存在を示すために非表示の領域の周りの線が表示されます。  
  
    2.  地域がクライアント制御またはでエディター制御するかどうかを指定、`dwBehavior`のメンバー、<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>構造体。 スマート アウトライン実装では、アウトラインのエディターとクライアントの制御と非表示テキスト領域の組み合わせを含めることができます。