---
title: "言語サービスとエディターを拡張 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4e81409f8ac93c80bf16b5040c6f388b64ffabbe
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="extending-the-editor-and-language-services"></a>エディターと言語サービスの拡張
言語サービスの機能 (IntelliSense) などを独自のエディターに追加して、Visual Studio code エディターのほとんどの機能を拡張できます。  拡張することができますの一覧については、次を参照してください。[言語サービスとエディター拡張機能ポイント](../extensibility/language-service-and-editor-extension-points.md)です。  
  
 ほとんどのエディターの機能を拡張するには、Managed Extensibility Framework (MEF) を使用します。 などの場合は、エディターの機能を拡張する場合は、構文の色分け、書き込めること、MEF*部品*対象となる別の色分けや処理なったら分類を定義します。 エディターには、同じ機能の複数の拡張機能もサポートしています。  
  
 エディターのプレゼンテーション層が基づく、Windows Presentation Framework (WPF)。 WPF では、柔軟なテキストの書式設定のグラフィックス ライブラリを提供しもグラフィックとアニメーションなどの視覚エフェクトを提供します。  
  
 Visual Studio SDK は、アダプターと呼ばれる*shim*以前のバージョン用に作成された Vspackage をサポートするためにします。 ただし、既存の VSPackage があればより優れたパフォーマンスと信頼性を取得する新しい技術を更新することお勧めします。  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[言語サービスとエディターの拡張機能の概要](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|エディターの拡張機能を作成する方法について説明します。|  
|[エディターの内部](../extensibility/inside-the-editor.md)|エディターの一般的な構造とその機能の一部を示しています。|  
|[エディター内の Managed Extensibility Framework](../extensibility/managed-extensibility-framework-in-the-editor.md)|エディターでは、Managed Extensibility Framework (MEF) を使用する方法について説明します。|  
|[言語サービスとエディターの拡張ポイント](../extensibility/language-service-and-editor-extension-points.md)|エディターの拡張点を一覧表示します。 拡張機能ポイントでは、拡張可能なエディター機能を表します。|  
|[チュートリアル: ビューの表示要素、コマンド、設定 (垂直グリッド ガイド) の作成](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|手順について説明し、コードを特定の表示幅を確保するための列 gudie 線を描画するビューの表示要素の構築を説明します。  読み取りと設定の書き込みだけでなく宣言とコマンド ウィンドウから呼び出すことのできるコマンドを実装することも表示されます。|  
|[エディターのインポート](../extensibility/editor-imports.md)|拡張機能をインポートするサービスの一覧を表示します。|  
|[エディターにレガシ コードを改変.](../extensibility/adapting-legacy-code-to-the-editor.md)|エディターを拡張する (前の Visual Studio 2010) のレガシ コードを改変するさまざまな方法について説明します。|  
|[従来の言語サービスの移行](../extensibility/internals/migrating-a-legacy-language-service.md)|基づく VSPackage では言語サービスを移行する方法について説明します。|  
|[チュートリアル: コンテンツの種類とファイル名拡張子とをリンクさせる](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|コンテンツの種類をファイル名拡張子にリンクする方法を示します。|  
|[チュートリアル: 余白のグリフの作成](../extensibility/walkthrough-creating-a-margin-glyph.md)|余白にアイコンを追加する方法を示します。|  
|[チュートリアル: テキストの強調表示](../extensibility/walkthrough-highlighting-text.md)|使用する方法を示します*タグ*テキストを強調表示します。|  
|[チュートリアル: アウトライン](../extensibility/walkthrough-outlining.md)|特定の種類の中かっこのアウトライン表示を追加する方法を示します。|  
|[チュートリアル: 対応するかっこの表示](../extensibility/walkthrough-displaying-matching-braces.md)|対応する中かっこを強調表示する方法を示します。|  
|[チュートリアル: クイック ヒントの表示](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|プロパティ、メソッド、およびイベントのようなコードの要素を記述するクイック ヒント ポップアップを表示する方法を示します。|  
|[チュートリアル: シグネチャ ヘルプの表示](../extensibility/walkthrough-displaying-signature-help.md)|シグネチャにパラメーターの型と数に関する情報を示すポップアップを表示する方法を示します。|  
|[チュートリアル: 入力候補の表示](../extensibility/walkthrough-displaying-statement-completion.md)|ステートメント入力候補を実装する方法を示します。|  
|[チュートリアル: コード スニペットの実装](../extensibility/walkthrough-implementing-code-snippets.md)|コード スニペットの拡張を実装する方法を示します。|  
|[チュートリアル: 電球アイコンによる提案の表示](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|電球コードについてのご提案を表示する方法を示します。|  
|[チュートリアル: エディター拡張機能でシェル コマンドを使用する](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|MEF コンポーネントを使用して、VSPackage でメニュー コマンドを関連付ける方法を示します。|  
|[チュートリアル: エディター拡張機能でショートカット キーを使用する](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|MEF コンポーネントを使用して、VSPackage でメニューのショートカットを関連付ける方法を示します。|  
|[MEF (Managed Extensibility Framework)](/dotnet/framework/mef/index)|Managed Extensibility Framework (MEF) についての情報を提供します。|  
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Windows Presentation Foundation (WPF) についての情報を提供します。|  
  
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