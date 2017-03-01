---
title: "エディターと言語サービスの拡張 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
caps.latest.revision: 22
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 4d04f4588b1005e9b5ccb42c6042d01aacb45710
ms.lasthandoff: 02/22/2017

---
# <a name="extending-the-editor-and-language-services"></a>エディターと言語サービスの拡張
独自のエディターに (IntelliSense) などの言語サービスの機能を追加し、Visual Studio コード エディターのほとんどの機能を拡張できます。  拡張することができますの一覧については、次を参照してください。[言語サービスとエディターの拡張ポイント](../extensibility/language-service-and-editor-extension-points.md)します。  
  
 ほとんどのエディターの機能を拡張するには、Managed Extensibility Framework (MEF) を使用します。 たとえば、拡張するエディター機能が構文の色分けの場合は、MEF を記述できます*コンポーネント パーツ*対象となる別の色付けとする処理済みとして分類を定義します。 エディターには、同じ機能の複数の拡張機能もサポートしています。  
  
 エディターのプレゼンテーション層がベース、Windows Presentation Framework (WPF)。 WPF では、柔軟性の高いテキストの書式設定のグラフィックス ライブラリを提供し、またグラフィックとアニメーションなどの視覚エフェクトを提供します。  
  
 Visual Studio SDK は、アダプターと呼ばれる*shim*以前のバージョン用に作成された VSPackages をサポートするためにします。 ただし、既存の vs パッケージがある場合は場合、より優れたパフォーマンスと信頼性を取得する新しいテクノロジに更新することを勧めします。  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[言語サービスとエディターの拡張機能の概要](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|エディターの拡張機能を作成する方法について説明します。|  
|[エディター内](../extensibility/inside-the-editor.md)|エディターの一般的な構造をについて説明し、その機能の一部を示します。|  
|[エディターで managed Extensibility Framework](../extensibility/managed-extensibility-framework-in-the-editor.md)|エディターでは、Managed Extensibility Framework (MEF) を使用する方法について説明します。|  
|[言語サービスとエディターの拡張ポイント](../extensibility/language-service-and-editor-extension-points.md)|エディターの拡張ポイントを一覧表示します。 拡張ポイントは、拡張可能なエディター機能を表します。|  
|[チュートリアル: ビューの表示要素、コマンド、および設定 (列ガイド) を作成します。](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|手順を説明し、コードを特定の表示幅を確保するための列 gudie 線を描画するビューの表示要素の構築を説明します。  読み取りと設定の書き込みだけでなくを宣言して、コマンド ウィンドウから呼び出すことのできるコマンドの実装にも表示されます。|  
|[エディターのインポート](../extensibility/editor-imports.md)|拡張機能をインポートできるサービスの一覧を表示します。|  
|[エディターにレガシ コードを改変](../extensibility/adapting-legacy-code-to-the-editor.md)|エディターを拡張する (事前 Visual Studio 2010) のレガシ コードを改変するさまざまな方法について説明します。|  
|[従来の言語サービスを移行します。](../extensibility/internals/migrating-a-legacy-language-service.md)|VSPackage ベース言語サービスに移行する方法をについて説明します。|  
|[チュートリアル: ファイル名拡張子へのコンテンツの種類のリンク](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|コンテンツの種類を拡張子のファイルにリンクする方法を示します。|  
|[チュートリアル: 余白のグリフの作成](../extensibility/walkthrough-creating-a-margin-glyph.md)|余白にアイコンを追加する方法を示します。|  
|[チュートリアル: テキストの強調表示](../extensibility/walkthrough-highlighting-text.md)|使用する方法を示しています*タグ*テキストを強調表示します。|  
|[チュートリアル: アウトラインの中止](../extensibility/walkthrough-outlining.md)|特定の種類の中かっこのアウトライン表示を追加する方法を示します。|  
|[チュートリアル: 対応する中かっこの表示](../extensibility/walkthrough-displaying-matching-braces.md)|対応する中かっこを強調表示する方法を示します。|  
|[チュートリアル: クイック ヒントの表示](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|プロパティ、メソッド、およびイベントのようなコードの要素について説明するクイック ヒント ポップアップを表示する方法を示します。|  
|[チュートリアル: シグニチャ ヘルプの表示](../extensibility/walkthrough-displaying-signature-help.md)|シグネチャにパラメーターの型と数に関する情報を示すポップアップを表示する方法を示します。|  
|[チュートリアル: 入力候補の表示](../extensibility/walkthrough-displaying-statement-completion.md)|ステートメント入力候補を実装する方法を示します。|  
|[チュートリアル: コード スニペットの実装](../extensibility/walkthrough-implementing-code-snippets.md)|コード スニペットの拡張を実装する方法を示します。|  
|[チュートリアル: 電球検索候補の表示](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|コードの検索候補の電球を表示する方法を示します。|  
|[チュートリアル: エディター拡張機能とシェル コマンドを使用します。](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|VSPackage でメニュー コマンドを MEF コンポーネントに関連付ける方法を示します。|  
|[チュートリアル: エディター拡張機能とショートカット キーを使用します。](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|VSPackage でメニューのショートカットを MEF コンポーネントに関連付ける方法を示します。|  
|[Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|マネージ機能拡張フレームワーク (MEF) についての情報を提供します。|  
|[Windows Presentation Foundation](http://msdn.microsoft.com/Library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Windows Presentation Foundation (WPF) についての情報を提供します。|  
  
## <a name="reference"></a>参照  
 Visual Studio エディターには、次の名前空間が含まれています。  
  
 <xref:Microsoft.VisualStudio.Language.Intellisense></xref:Microsoft.VisualStudio.Language.Intellisense>  
  
 <xref:Microsoft.VisualStudio.Language.StandardClassification></xref:Microsoft.VisualStudio.Language.StandardClassification>  
  
 <xref:Microsoft.VisualStudio.Editor></xref:Microsoft.VisualStudio.Editor>  
  
 <xref:Microsoft.VisualStudio.Text></xref:Microsoft.VisualStudio.Text>  
  
 <xref:Microsoft.VisualStudio.Text.Adornments></xref:Microsoft.VisualStudio.Text.Adornments>  
  
 <xref:Microsoft.VisualStudio.Text.Classification></xref:Microsoft.VisualStudio.Text.Classification>  
  
 <xref:Microsoft.VisualStudio.Text.Differencing></xref:Microsoft.VisualStudio.Text.Differencing>  
  
 <xref:Microsoft.VisualStudio.Text.Document></xref:Microsoft.VisualStudio.Text.Document>  
  
 <xref:Microsoft.VisualStudio.Text.Editor></xref:Microsoft.VisualStudio.Text.Editor>  
  
 <xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods></xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods>  
  
 <xref:Microsoft.VisualStudio.Text.Formatting></xref:Microsoft.VisualStudio.Text.Formatting>  
  
 <xref:Microsoft.VisualStudio.Text.IncrementalSearch></xref:Microsoft.VisualStudio.Text.IncrementalSearch>  
  
 <xref:Microsoft.VisualStudio.Text.Operations></xref:Microsoft.VisualStudio.Text.Operations>  
  
 <xref:Microsoft.VisualStudio.Text.Outlining></xref:Microsoft.VisualStudio.Text.Outlining>  
  
 <xref:Microsoft.VisualStudio.Text.Projection></xref:Microsoft.VisualStudio.Text.Projection>  
  
 <xref:Microsoft.VisualStudio.Text.Tagging></xref:Microsoft.VisualStudio.Text.Tagging>  
  
 <xref:Microsoft.VisualStudio.Utilities></xref:Microsoft.VisualStudio.Utilities>
