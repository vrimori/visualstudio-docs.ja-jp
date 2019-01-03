---
title: 構文のカスタム エディターで色分け |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f82902ebcb82ea311617d3a7a767c5dabaedd311
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53886651"
---
# <a name="syntax-coloring-in-custom-editors"></a>カスタム エディターでの構文の色分け表示
Visual Studio 環境の SDK エディターなどのコア エディターは、構文の特定の項目を識別し、特定のドキュメント ビューの指定した色で表示する言語サービスを使用します。

## <a name="colorization-requirements"></a>色づけの要件
 すべてのエディターの言語サービスの colorizer を実装する必要があります。

1.  実装するオブジェクトを使用して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>テキストの色で表示されますおよび実装するオブジェクトを管理する<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>テキストのドキュメント ビューを提供します。

2.  言語サービスの特定の GUID を使用して、VSPackage のサービス プロバイダーのクエリを実行して、特定の言語サービスへのインターフェイスを取得します。

3.  呼び出す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>メソッドを実装するオブジェクトの<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>します。 このメソッドは、使用して、言語サービスを関連付けます、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>色で表示されますが、テキストを管理する VSPackage を使用して実装します。

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>言語サービスの Colorizer のコア エディターの使用状況
 コア エディター、解析および言語サービスの colorizer によるテキストのレンダリングのインスタンスによって、colorizer の言語サービスを取得する場合は、さらに、一部の介入を必要とせずに自動的に発生します。

 IDE に透過的に。

-   呼び出しを解析し、テキストの分析が追加または変更の実装では、必要に応じて colorizer<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>します。

-   提供されるドキュメント ビューによって提供される表示により、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>実装が更新され、colorizer によって返される情報を使用して再描画します。

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>言語サービスの Colorizer の非コア エディターの使用状況
 非コア エディター インスタンスでは、言語サービスの構文の色づけのサービスを使用できますもが、必要があります明示的に取得し適用、サービスの colorizer のドキュメント ビュー自体を再描画します。

 これを行うには、非コア エディターが必要です。

1.  言語サービスの colorizer オブジェクトを取得します (実装<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>と<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>)。 VSPackage は呼び出すことによって、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>言語サービスのインターフェイスのメソッド。

2.  呼び出す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>テキストの特定の範囲の一覧を要求するメソッド。

     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>メソッドは値の配列を返します、色分けされて表示される span の各文字のテキストに 1 つ。 また、コメント、キーワード、またはデータ型などの装飾が可能な項目の特定の種類としてテキスト範囲を識別します。

3.  によって返される色づけの情報を使用して<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>を再描画し、そのテキストが表示されます。

> [!NOTE]
> 言語サービスの colorizer だけでなく、VSPackage は、汎用的な Visual Studio 環境の SDK のテキストの色指定メカニズムを使用してが選択できます。 このメカニズムの詳細については、次を参照してください。[を使用してフォントおよび色](../extensibility/using-fonts-and-colors.md)します。

## <a name="see-also"></a>関連項目

- [従来の言語サービスでの構文の色分け表示](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [構文の色分け表示の実装](../extensibility/internals/implementing-syntax-coloring.md)
- [方法: 組み込みの配色可能な項目を使用して、](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [カスタムの配色可能な項目](../extensibility/internals/custom-colorable-items.md)