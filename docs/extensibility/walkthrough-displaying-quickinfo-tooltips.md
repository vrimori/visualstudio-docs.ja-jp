---
title: 'チュートリアル: クイック ヒントの表示 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 42ad89e544727a67611a305444f85ff022f6b2ff
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500031"
---
# <a name="walkthrough-display-quickinfo-tooltips"></a>チュートリアル: 表示クイック ヒント
クイック ヒントはメソッド シグネチャを表示する IntelliSense 機能である説明と、ユーザーがポインターをメソッド名の上に移動します。 クイック ヒントの説明を提供する識別子を定義し、コンテンツを表示するツールヒントを作成し、クイック ヒントなど、言語ベースの機能を実装できます。 クイック ヒントを定義するには、言語サービスのコンテキストでまたは独自ファイル名拡張子とコンテンツ タイプを定義し、その型だけのクイック ヒントを表示できますか ("text") などの既存のコンテンツ タイプのクイック ヒントを表示することができます。 このチュートリアルでは、「テキスト」コンテンツ タイプのクイック ヒントを表示する方法を示します。  
  
 クイック ヒントの例では、このチュートリアルは、ユーザーは、メソッド名の上、ポインターを移動すると、ツールヒントを表示します。 この設計では、これら 4 つのインターフェイスを実装する必要があります。  
  
-   ソース インターフェイス  
  
-   ソース プロバイダーのインターフェイス  
  
-   コント ローラーのインターフェイス  
  
-   コント ローラーのプロバイダー インターフェイス  
  
 ソースとコント ローラーのプロバイダーは Managed Extensibility Framework (MEF) コンポーネント パーツ、ソースとコント ローラー クラスをエクスポートする責任を負います、サービスのインポートしブローカーなど、<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>ツールヒントのテキストを作成します。バッファー、および<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>、QuickInfo セッションが開始します。  
  
 この例でクイック ヒントのソースがメソッドの名前と説明については、ハード コーディングされた一覧には、完全な実装で、言語サービスと言語のドキュメントがそのコンテンツを提供する責任を負います。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降で、ダウンロード センターから、Visual Studio SDK をインストールする必要はありません。 Visual Studio のセットアップのオプション機能として含まれています。 また、後から VS SDK をインストールすることもできます。 詳細については、次を参照してください。 [Visual Studio SDK をインストール](../extensibility/installing-the-visual-studio-sdk.md)します。  
  
## <a name="create-a-mef-project"></a>MEF プロジェクトを作成します。  
  
### <a name="to-create-a-mef-project"></a>MEF プロジェクトを作成するには  
  
1.  C# VSIX プロジェクトを作成します。 (で、**新しいプロジェクト**ダイアログ ボックスで、 **Visual c#/機能拡張**、し**VSIX プロジェクト**)。ソリューションの名前を`QuickInfoTest`します。  
  
2.  エディター分類子の項目テンプレートをプロジェクトに追加します。 詳細については、次を参照してください。[エディターの項目テンプレートを使用した拡張機能を作成する](../extensibility/creating-an-extension-with-an-editor-item-template.md)します。  
  
3.  既存のクラス ファイルを削除します。  
  
## <a name="implement-the-quickinfo-source"></a>QuickInfo ソースを実装します。  
 QuickInfo ソースは、識別子とその説明のセットを収集し、識別子のいずれかが発生したときに、ツールヒントのテキスト バッファーにコンテンツを追加します。 この例でソース コンス トラクターで、識別子とその説明はだけ追加します。  
  
#### <a name="to-implement-the-quickinfo-source"></a>QuickInfo ソースを実装するには  
  
1.  クラス ファイルを追加し、名前`TestQuickInfoSource`します。  
  
2.  参照を追加*Microsoft.VisualStudio.Language.IntelliSense*します。  
  
3.  次の imports を追加します。  
  
     [!code-vb[VSSDKQuickInfoTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb)]
     [!code-csharp[VSSDKQuickInfoTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]  
  
4.  実装するクラスを宣言<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>、名前を付けます`TestQuickInfoSource`します。  
  
     [!code-vb[VSSDKQuickInfoTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb)]
     [!code-csharp[VSSDKQuickInfoTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]  
  
5.  QuickInfo ソース プロバイダー、テキスト バッファーと、一連のメソッド名とメソッドのシグネチャのフィールドを追加します。 この例でメソッドの名前とシグネチャを初期化します。、`TestQuickInfoSource`コンス トラクター。  
  
     [!code-vb[VSSDKQuickInfoTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb)]
     [!code-csharp[VSSDKQuickInfoTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]  
  
6.  クイック ヒントのソース プロバイダーと、テキスト バッファーを設定し、メソッド名、およびメソッド シグネチャと説明のセットを設定するコンス トラクターを追加します。  
  
     [!code-vb[VSSDKQuickInfoTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb)]
     [!code-csharp[VSSDKQuickInfoTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]  
  
7.  <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A> メソッドを実装します。 この例で、メソッド、現在の単語または検索前の単語、カーソルが行またはテキスト バッファーの末尾にある場合します。 単語がメソッド名のいずれかである場合、そのメソッド名の説明は、クイック ヒントのコンテンツに追加されます。  
  
     [!code-vb[VSSDKQuickInfoTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb)]
     [!code-csharp[VSSDKQuickInfoTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]  
  
8.  以降、Dispose() メソッドを実装することも必要があります<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>実装<xref:System.IDisposable>:。  
  
     [!code-vb[VSSDKQuickInfoTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb)]
     [!code-csharp[VSSDKQuickInfoTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]  
  
## <a name="implement-a-quickinfo-source-provider"></a>クイック ヒントのソース プロバイダーを実装します。  
 QuickInfo ソースのプロバイダーは、主に自体を MEF コンポーネントの一部としてエクスポートし、クイック ヒントのソースをインスタンス化は機能します。 MEF コンポーネントの一部であるために、他の MEF コンポーネント パーツをインポートできます。  
  
#### <a name="to-implement-a-quickinfo-source-provider"></a>QuickInfo ソース プロバイダーを実装するには  
  
1.  という名前の QuickInfo ソース プロバイダーを宣言`TestQuickInfoSourceProvider`を実装する<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>、およびエクスポートして、 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "ツールヒント QuickInfo Source"の<xref:Microsoft.VisualStudio.Utilities.OrderAttribute>の Before ="default"と<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>"text"の。  
  
     [!code-vb[VSSDKQuickInfoTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb)]
     [!code-csharp[VSSDKQuickInfoTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]  
  
2.  2 つのエディター サービスをインポート<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>と<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>のプロパティとして`TestQuickInfoSourceProvider`します。  
  
     [!code-vb[VSSDKQuickInfoTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb)]
     [!code-csharp[VSSDKQuickInfoTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]  
  
3.  実装<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A>を返す新しい`TestQuickInfoSource`します。  
  
     [!code-vb[VSSDKQuickInfoTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb)]
     [!code-csharp[VSSDKQuickInfoTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]  
  
## <a name="implement-a-quickinfo-controller"></a>QuickInfo コント ローラーを実装します。  
 QuickInfo コント ローラーは、クイック ヒントが表示される場合を決定します。 この例で、クイック ヒントは、ポインターがメソッド名のいずれかに対応する単語が表示されます。 QuickInfo コント ローラーは、クイック ヒントのセッションをトリガーする、マウス ホバー イベント ハンドラーを実装します。  
  
### <a name="to-implement-a-quickinfo-controller"></a>QuickInfo コント ローラーを実装するには  
  
1.  実装するクラスを宣言<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>、名前を付けます`TestQuickInfoController`します。  
  
     [!code-vb[VSSDKQuickInfoTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb)]
     [!code-csharp[VSSDKQuickInfoTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]  
  
2.  テキスト ビュー、QuickInfo セッション、およびクイック ヒントのコント ローラーのプロバイダーで表されるテキスト バッファーのテキスト ビューで、プライベート フィールドを追加します。  
  
     [!code-vb[VSSDKQuickInfoTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb)]
     [!code-csharp[VSSDKQuickInfoTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]  
  
3.  フィールドを設定し、マウス ホバー イベント ハンドラーを追加するコンス トラクターを追加します。  
  
     [!code-vb[VSSDKQuickInfoTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb)]
     [!code-csharp[VSSDKQuickInfoTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]  
  
4.  QuickInfo セッションをトリガーするマウス ホバー イベント ハンドラーを追加します。  
  
     [!code-vb[VSSDKQuickInfoTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb)]
     [!code-csharp[VSSDKQuickInfoTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]  
  
5.  実装、<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A>メソッドをコント ローラーが、テキスト ビューからデタッチされると、マウス ホバー イベント ハンドラーを削除します。  
  
     [!code-vb[VSSDKQuickInfoTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb)]
     [!code-csharp[VSSDKQuickInfoTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]  
  
6.  実装、<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A>メソッドと<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A>この例では空のメソッドとしてメソッド。  
  
     [!code-vb[VSSDKQuickInfoTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb)]
     [!code-csharp[VSSDKQuickInfoTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]  
  
## <a name="implementing-the-quickinfo-controller-provider"></a>QuickInfo コント ローラーのプロバイダーを実装します。  
 QuickInfo コント ローラーのプロバイダー自体を MEF コンポーネントの一部としてエクスポートおよび QuickInfo コント ローラーをインスタンス化する主な役割を果たします。 MEF コンポーネントの一部であるために、他の MEF コンポーネント パーツをインポートできます。  
  
### <a name="to-implement-the-quickinfo-controller-provider"></a>QuickInfo コント ローラーのプロバイダーを実装するには  
  
1.  という名前のクラスを宣言`TestQuickInfoControllerProvider`を実装する<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>でエクスポートし、 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> 「ツールヒント QuickInfo コント ローラー」の<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>"text"。  
  
     [!code-vb[VSSDKQuickInfoTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb)]
     [!code-csharp[VSSDKQuickInfoTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]  
  
2.  インポート、<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>プロパティとして。  
  
     [!code-vb[VSSDKQuickInfoTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb)]
     [!code-csharp[VSSDKQuickInfoTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]  
  
3.  実装、 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> QuickInfo コント ローラーをインスタンス化するメソッド。  
  
     [!code-vb[VSSDKQuickInfoTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb)]
     [!code-csharp[VSSDKQuickInfoTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]  
  
## <a name="build-and-test-the-code"></a>ビルドし、コードのテスト  
 このコードをテストするには、QuickInfoTest ソリューションをビルドし、実験用インスタンスで実行します。  
  
### <a name="to-build-and-test-the-quickinfotest-solution"></a>ビルドして QuickInfoTest ソリューションをテストするには  
  
1.  ソリューションをビルドします。  
  
2.  デバッガーでこのプロジェクトを実行する場合は、Visual Studio の 2 番目のインスタンスが開始します。  
  
3.  テキスト ファイルと型がいくつかのテキストの単語を含む"add"および「減算」を作成します。  
  
4.  「追加」の出現回数の 1 つにマウス ポインターを移動します。 署名との説明、`add`メソッドを表示する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: コンテンツの種類をファイル名拡張子にリンクします。](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)