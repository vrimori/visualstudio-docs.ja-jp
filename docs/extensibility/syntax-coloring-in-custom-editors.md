---
title: カスタム エディターの構文の色分け |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 18e087e82754244b7abda530f733a6047447f4a7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139462"
---
# <a name="syntax-coloring-in-custom-editors"></a>カスタム エディターの構文の色分け
コア エディターなど、visual Studio 環境 SDK エディターは、構文上の特定の項目を識別し、特定のドキュメント ビューの指定した色で表示する言語サービスを使用します。

## <a name="colorization-requirements"></a>色付け要件
 すべてのエディターが言語サービスの colorizer を実装する必要があります。

1.  実装するオブジェクトを使用して<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>色で表示するテキストと実装するオブジェクトを管理する<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>テキストのドキュメントを確認することです。

2.  言語サービスの識別する GUID を使用して、VSPackage のサービス プロバイダーのクエリを実行して特定の言語サービスへのインターフェイスを取得します。

3.  呼び出す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>メソッドを実装するオブジェクトの<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>します。 このメソッドは、使用して、言語サービスを関連付けます、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>色で表示されるテキストを管理する VSPackage を使用して実装します。

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>言語サービスの Colorizer のコア エディターの使用方法
 コア エディター、解析および言語サービスの colorizer によるテキストのレンダリングのインスタンスによって、colorizer に言語サービスを取得する場合は、さらに、一部の介入を必要とせずに自動的に発生します。

 IDE に透過的にします。

-   呼び出しを解析し、テキストの分析が追加または変更の実装で colorizer に応じて<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>です。

-   提供されるドキュメント ビューによって提供される表示により、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>実装が更新され、colorizer によって返される情報を使用して再描画します。

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>言語サービスの Colorizer の非コア エディターの使用方法
 非コア エディター インスタンスことができますもを使用言語サービスの構文の色づけサービスが必要があります明示的に取得およびサービスの colorizer を適用、ドキュメント ビュー自体を再描画します。

 これを行うには、非コア エディターでは次の必要があります。

1.  言語サービスの colorizer オブジェクトを取得します (を実装する<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>と<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>)。 VSPackage は、呼び出すことによって、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>言語サービスのインターフェイスのメソッドです。

2.  呼び出す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>テキストの特定範囲の一覧を要求するメソッド。

     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>メソッドの値の配列を返します、色分け表示されているにまたがるテキストでは、各文字を 1 つです。 また、コメント、キーワード、またはデータ型などの装飾が可能な項目の特定の型としてのテキスト範囲を識別します。

3.  によって返される色付け情報を使用して<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>を再描画し、そのテキストが表示されます。

> [!NOTE]
> 言語サービスの colorizer 以外にも、VSPackage が、汎用的な Visual Studio 環境 SDK テキストの色指定メカニズムを使用できます。 このメカニズムの詳細については、次を参照してください。[を使用するフォントおよび色](../extensibility/using-fonts-and-colors.md)です。

## <a name="see-also"></a>関連項目

- [従来の言語サービスでの構文の色分け表示](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [構文の色分け表示の実装](../extensibility/internals/implementing-syntax-coloring.md)
- [方法: ビルトインの配色可能な項目の使用](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [カスタムの配色可能な項目](../extensibility/internals/custom-colorable-items.md)