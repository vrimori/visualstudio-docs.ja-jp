---
title: エディターと言語サービスの拡張 |Microsoft Docs
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
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 91eab151680d936c350c8c5745aec6c9fe86e47c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51723072"
---
# <a name="extending-the-editor-and-language-services"></a>エディターと言語サービスの拡張
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

独自のエディターに (IntelliSense) などの言語サービスの機能を追加し、Visual Studio コード エディターのほとんどの機能を拡張できます。  拡張することができますの完全な一覧を参照してください。[言語サービスとエディターの拡張ポイント](../extensibility/language-service-and-editor-extension-points.md)します。  
  
 ほとんどのエディター機能を拡張するには、Managed Extensibility Framework (MEF) を使用します。 たとえば、エディター機能を拡張するが構文の色分け表示の場合は、MEF を記述できます*コンポーネント パーツ*分類する別の色分け表示と処理にする方法を定義します。 エディターには、同じ機能の複数の拡張機能もサポートしています。  
  
 エディターのプレゼンテーション層に基づく、Windows Presentation Framework (WPF)。 WPF では、柔軟なテキストの書式設定のグラフィックス ライブラリを提供しもグラフィックスとアニメーションなどの視覚エフェクトを提供します。  
  
 Visual Studio SDK は、アダプターと呼ばれる*shim*以前のバージョン用に作成された Vspackage をサポートするためにします。 ただし、既存の VSPackage があればより優れたパフォーマンスと信頼性を取得する新しいテクノロジに更新することお勧めします。  
  
## <a name="related-topics"></a>関連トピック  
  
|Title|説明|  
|-----------|-----------------|  
|[言語サービスとエディターの拡張機能の概要](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|エディターの拡張機能を作成する方法について説明します。|  
|[エディターの内部](../extensibility/inside-the-editor.md)|エディターの一般的な構造を説明し、その機能の一部を示します。|  
|[エディター内の Managed Extensibility Framework](../extensibility/managed-extensibility-framework-in-the-editor.md)|エディターでの Managed Extensibility Framework (MEF) を使用する方法について説明します。|  
|[言語サービスとエディターの拡張ポイント](../extensibility/language-service-and-editor-extension-points.md)|エディターの拡張ポイントを一覧表示します。 拡張機能ポイントは、拡張可能なエディター機能を表します。|  
|[チュートリアル: ビューの表示要素、コマンド、設定 (垂直グリッド ガイド) の作成](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|手順について説明し、コードを特定の表示幅を確保するための列 gudie 線を描画するビューの表示要素の構築について説明します。  読み取りと設定の書き込みだけでなくを宣言して、コマンド ウィンドウから呼び出すことができるコマンドの実装にも表示されます。|  
|[エディターのインポート](../extensibility/editor-imports.md)|拡張機能をインポートするサービスの一覧を表示します。|  
|[レガシ コードをエディターに適合させる](../extensibility/adapting-legacy-code-to-the-editor.md)|エディターを拡張する (事前に Visual Studio 2010) のレガシ コードを改変するさまざまな方法について説明します。|  
|[従来の言語サービスの移行](../extensibility/internals/migrating-a-legacy-language-service.md)|基づく VSPackage での言語サービスを移行する方法について説明します。|  
|[チュートリアル: コンテンツの種類とファイル名拡張子とをリンクさせる](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|コンテンツの種類をファイル名拡張子にリンクする方法を示しています。|  
|[チュートリアル: 余白のグリフの作成](../extensibility/walkthrough-creating-a-margin-glyph.md)|余白にアイコンを追加する方法を示します。|  
|[チュートリアル: テキストの強調表示](../extensibility/walkthrough-highlighting-text.md)|使用する方法を示します*タグ*テキストを強調表示します。|  
|[チュートリアル: アウトライン](../extensibility/walkthrough-outlining.md)|特定の種類の中かっこのアウトラインを追加する方法を示します。|  
|[チュートリアル: 対応するかっこの表示](../extensibility/walkthrough-displaying-matching-braces.md)|対応する中かっこを強調表示する方法を示します。|  
|[チュートリアル: クイック ヒントの表示](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|プロパティ、メソッド、およびイベントなどのコードの要素について説明するクイック ヒント ポップアップを表示する方法を示します。|  
|[チュートリアル: シグネチャ ヘルプの表示](../extensibility/walkthrough-displaying-signature-help.md)|シグネチャのパラメーターの型と数に関する情報を提供するポップアップを表示する方法を示します。|  
|[チュートリアル: 入力候補の表示](../extensibility/walkthrough-displaying-statement-completion.md)|ステートメント入力候補を実装する方法を示します。|  
|[チュートリアル: コード スニペットの実装](../extensibility/walkthrough-implementing-code-snippets.md)|コード スニペットの展開を実装する方法を示します。|  
|[チュートリアル: 電球アイコンによる提案の表示](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|コード修正候補の電球を表示する方法を示します。|  
|[チュートリアル: エディター拡張機能でシェル コマンドを使用する](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|VSPackage にメニュー コマンドを MEF コンポーネントと関連付ける方法を示しています。|  
|[チュートリアル: エディター拡張機能でショートカット キーを使用する](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|VSPackage でのメニューのショートカットを MEF コンポーネントに関連付ける方法を示しています。|  
|[MEF (Managed Extensibility Framework)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Managed Extensibility Framework (MEF) についての情報を提供します。|  
|[Windows Presentation Foundation](http://msdn.microsoft.com/library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Windows Presentation Foundation (WPF) についての情報を提供します。|  
  
## <a name="reference"></a>参照  
 Visual Studio エディターには、次の名前空間が含まれています。  
  
 <xref:Microsoft.VisualStudio.Language.Intellisense>  
  
 <xref:Microsoft.VisualStudio.Language.StandardClassification>  
  
 <xref:Microsoft.VisualStudio.Editor>  
  
 <xref:Microsoft.VisualStudio.Text>  
  
 <xref:Microsoft.VisualStudio.Text.Adornments>  
  
 <xref:Microsoft.VisualStudio.Text.Classification>  
  
 <xref:Microsoft.VisualStudio.Text.Differencing>  
  
 <xref:Microsoft.VisualStudio.Text.Document>  
  
 <xref:Microsoft.VisualStudio.Text.Editor>  
  
 <xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods>  
  
 <xref:Microsoft.VisualStudio.Text.Formatting>  
  
 <xref:Microsoft.VisualStudio.Text.IncrementalSearch>  
  
 <xref:Microsoft.VisualStudio.Text.Operations>  
  
 <xref:Microsoft.VisualStudio.Text.Outlining>  
  
 <xref:Microsoft.VisualStudio.Text.Projection>  
  
 <xref:Microsoft.VisualStudio.Text.Tagging>  
  
 <xref:Microsoft.VisualStudio.Utilities>

