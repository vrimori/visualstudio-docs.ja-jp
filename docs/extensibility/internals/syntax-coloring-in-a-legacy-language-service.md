---
title: 従来の言語サービスの構文の色分け |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 172f06f4e30f1320b6e17332cb2b54af91f7ed01
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31136056"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>従来の言語サービスの構文の色分け

Visual Studio では、言語の要素を識別し、エディターで指定された色で表示する色分けサービスを使用します。

## <a name="colorizer-model"></a>Colorizer モデル
 言語サービスを実装して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>がエディターを使用しているインターフェイス。 この実装は、次の図に示すように、言語サービスから別のオブジェクトを示します。

 ![SVC Colorizer グラフィック](../../extensibility/internals/media/figlgsvccolorizer.gif)

> [!NOTE]
>  構文の色分けをサービスとは別のテキストを色分け [全般]、Visual Studio メカニズムです。 [全般] の詳細については[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]色分けをサポートするメカニズムを参照してください[を使用するフォントおよび色](../../extensibility/using-fonts-and-colors.md)です。

 言語サービスは、colorizer だけでなくカスタムの装飾が可能な項目が用意されている広告によって、エディターで使用されるカスタムの装飾が可能な項目を指定できます。 実装することによってこれを行う、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>インターフェイスを実装する、同じオブジェクトに対して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>インターフェイスです。 エディターを呼び出すときは、カスタムの装飾が可能な項目の数を返します、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A>メソッド、およびそのエディターを呼び出すと、個々 のカスタムの装飾が可能な項目を返します、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>メソッドです。

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>メソッドを実装するオブジェクトを返します、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>インターフェイスです。 これを実装する必要があります、言語サービスは、24 ビット、または高の色の値をサポートする場合、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>インターフェイスと同じオブジェクトを<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>インターフェイスです。

## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>VSPackage が言語サービス Colorizer を使用する方法

1.  VSPackage では、言語サービスには、次の VSPackage を必要とする、適切な言語サービスを取得する必要があります。

    1.  実装するオブジェクトを使用して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>色で表示するテキストを取得するインターフェイスです。

         テキストが通常表示されるを実装するオブジェクトを使用して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>インターフェイスです。

    2.  言語サービス GUID の VSPackage のサービス プロバイダーのクエリを実行して、言語サービスを取得します。 言語サービスは、レジストリでファイル拡張子によって識別されます。

    3.  使用して、言語サービスに関連付ける、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>を呼び出してその<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>メソッドです。

2.  VSPackage は、今すぐ入手し、colorizer オブジェクトは次のように使用できます。

    > [!NOTE]
    > コア エディターを使用して Vspackage を言語サービスの colorizer オブジェクトを明示的に取得する必要はありません。 コア エディターのインスタンスは、適切な言語サービスを取得するとすぐには、次に示すすべての色づけタスクを実行します。

    1.  実装する言語サービスの colorizer オブジェクトを取得、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>、および<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>インターフェイスを呼び出すことによって、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>メソッドを言語サービスの<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>オブジェクト。

    2.  呼び出す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>テキストの特定の範囲の colorizer 情報を取得します。

         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 色分け表示されているテキストの範囲内の各文字のいずれかの値の配列を返します。 値は、コア エディターで管理されている既定の装飾が可能な項目リストまたは言語サービス自体によって管理されるカスタムの装飾が可能な項目リストのいずれかである装飾が可能な項目のリストにインデックスです。

    3.  によって返される色付け情報を使用して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>メソッドを選択したテキストを表示します。

> [!NOTE]
>  言語サービス colorizer を使用するだけでなく、VSPackage は、汎用的な Visual Studio テキストが色分け表示メカニズムにも使用できます。 このメカニズムの詳細については、次を参照してください。[を使用するフォントおよび色](../../extensibility/using-fonts-and-colors.md)です。

## <a name="in-this-section"></a>このセクションの内容
 [構文の色分けを実装する](../../extensibility/internals/implementing-syntax-coloring.md)エディターで、言語サービスの構文の色分けや構文の色分けをサポートするためにどのような言語サービスを実装する必要がありますがどのようにアクセスする方法について説明します。

 [方法: 組み込みの装飾が可能な項目を使用して](../../extensibility/internals/how-to-use-built-in-colorable-items.md)言語サービスからの組み込みの装飾が可能な項目を使用する方法を示します。

 [カスタムの装飾が可能な項目](../../extensibility/internals/custom-colorable-items.md)カスタムの装飾が可能なアイテムを実装する方法について説明します。

## <a name="see-also"></a>関連項目

- [フォントおよび色を使用します。](../../extensibility/using-fonts-and-colors.md)