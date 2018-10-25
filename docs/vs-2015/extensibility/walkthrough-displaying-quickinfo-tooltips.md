---
title: 'チュートリアル: クイック ヒントの表示 |Microsoft Docs'
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
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c217426d4186477f22a21c9348ff30e181faa840
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863283"
---
# <a name="walkthrough-displaying-quickinfo-tooltips"></a>チュートリアル: クイック ヒントの表示
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

クイック ヒントはメソッド シグネチャを表示する IntelliSense 機能である説明と、ユーザーがポインターをメソッド名の上に移動します。 クイック ヒントの説明を提供する識別子を定義し、コンテンツを表示するツールヒントを作成し、クイック ヒントなど、言語ベースの機能を実装できます。 クイック ヒントを定義するには、言語サービスのコンテキストでまたは独自ファイル名拡張子とコンテンツ タイプを定義し、その型だけのクイック ヒントを表示できますか ("text") などの既存のコンテンツ タイプのクイック ヒントを表示することができます。 このチュートリアルでは、「テキスト」コンテンツ タイプのクイック ヒントを表示する方法を示します。  
  
 クイック ヒントの例では、このチュートリアルは、ユーザーは、メソッド名の上、ポインターを移動すると、ツールヒントを表示します。 この設計では、これら 4 つのインターフェイスを実装する必要があります。  
  
- ソース インターフェイス  
  
- ソース プロバイダーのインターフェイス  
  
- コント ローラーのインターフェイス  
  
- コント ローラーのプロバイダー インターフェイス  
  
  ソースとコント ローラーのプロバイダーは Managed Extensibility Framework (MEF) コンポーネント パーツ、ソースとコント ローラー クラスをエクスポートする責任を負います、サービスのインポートしブローカーなど、<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>ツールヒントのテキストを作成します。バッファー、および<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>、QuickInfo セッションが開始します。  
  
  この例でクイック ヒントのソースがメソッドの名前と説明については、ハード コーディングされた一覧には、完全な実装で、言語サービスと言語のドキュメントがそのコンテンツを提供する責任を負います。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="creating-a-mef-project"></a>MEF プロジェクトを作成します。  
  
#### <a name="to-create-a-mef-project"></a>MEF プロジェクトを作成するには  
  
1.  C# VSIX プロジェクトを作成します。 (で、**新しいプロジェクト**ダイアログ ボックスで、 **Visual c#/機能拡張**、し**VSIX プロジェクト**)。ソリューション `QuickInfoTest`の名前を指定します。  
  
2.  エディター分類子の項目テンプレートをプロジェクトに追加します。 詳細については、次を参照してください。[エディターの項目テンプレートを使用した拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)です。  
  
3.  既存のクラス ファイルを削除します。  
  
## <a name="implementing-the-quickinfo-source"></a>QuickInfo ソースの実装  
 QuickInfo ソースは、識別子とその説明のセットを収集し、識別子のいずれかが発生したときに、ツールヒントのテキスト バッファーにコンテンツを追加します。 この例でソース コンス トラクターで、識別子とその説明はだけ追加します。  
  
#### <a name="to-implement-the-quickinfo-source"></a>QuickInfo ソースを実装するには  
  
1.  クラス ファイルを追加し、その名前を `TestQuickInfoSource`にします。  
  
2.  Microsoft.VisualStudio.Language.IntelliSense への参照を追加します。  
  
3.  次の imports を追加します。  
  
     [!code-csharp[VSSDKQuickInfoTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#1)]
     [!code-vb[VSSDKQuickInfoTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#1)]  
  
4.  実装するクラスを宣言<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>、名前を付けます`TestQuickInfoSource`します。  
  
     [!code-csharp[VSSDKQuickInfoTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#2)]
     [!code-vb[VSSDKQuickInfoTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#2)]  
  
5.  QuickInfo ソース プロバイダー、テキスト バッファーと、一連のメソッド名とメソッドのシグネチャのフィールドを追加します。 この例でメソッドの名前とシグネチャを初期化します。、`TestQuickInfoSource`コンス トラクター。  
  
     [!code-csharp[VSSDKQuickInfoTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#3)]
     [!code-vb[VSSDKQuickInfoTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#3)]  
  
6.  クイック ヒントのソース プロバイダーと、テキスト バッファーを設定し、メソッド名、およびメソッド シグネチャと説明のセットを設定するコンス トラクターを追加します。  
  
     [!code-csharp[VSSDKQuickInfoTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#4)]
     [!code-vb[VSSDKQuickInfoTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#4)]  
  
7.  <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A> メソッドを実装します。 この例で、メソッド、現在の単語または検索前の単語、カーソルが行またはテキスト バッファーの末尾にある場合します。 単語がメソッド名のいずれかである場合、そのメソッド名の説明は、クイック ヒントのコンテンツに追加されます。  
  
     [!code-csharp[VSSDKQuickInfoTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#5)]
     [!code-vb[VSSDKQuickInfoTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#5)]  
  
8.  以降、Dispose() メソッドを実装することも必要があります<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>実装<xref:System.IDisposable>:。  
  
     [!code-csharp[VSSDKQuickInfoTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#6)]
     [!code-vb[VSSDKQuickInfoTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#6)]  
  
## <a name="implementing-a-quickinfo-source-provider"></a>QuickInfo ソース プロバイダーを実装します。  
 QuickInfo ソースのプロバイダーは、主に自体を MEF コンポーネントの一部としてエクスポートし、クイック ヒントのソースをインスタンス化は機能します。 MEF コンポーネントの一部であるために、他の MEF コンポーネント パーツをインポートできます。  
  
#### <a name="to-implement-a-quickinfo-source-provider"></a>QuickInfo ソース プロバイダーを実装するには  
  
1.  という名前の QuickInfo ソース プロバイダーを宣言`TestQuickInfoSourceProvider`を実装する<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>、およびエクスポートして、 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "ツールヒント QuickInfo Source"の<xref:Microsoft.VisualStudio.Utilities.OrderAttribute>の Before ="default"と<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>"text"の。  
  
     [!code-csharp[VSSDKQuickInfoTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#7)]
     [!code-vb[VSSDKQuickInfoTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#7)]  
  
2.  2 つのエディター サービスをインポート<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>と<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>のプロパティとして`TestQuickInfoSourceProvider`します。  
  
     [!code-csharp[VSSDKQuickInfoTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#8)]
     [!code-vb[VSSDKQuickInfoTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#8)]  
  
3.  実装<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A>を返す新しい`TestQuickInfoSource`します。  
  
     [!code-csharp[VSSDKQuickInfoTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#9)]
     [!code-vb[VSSDKQuickInfoTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#9)]  
  
## <a name="implementing-a-quickinfo-controller"></a>QuickInfo コント ローラーの実装  
 QuickInfo コント ローラーは、クイック ヒントを表示するかを決定します。 この例では、ポインターがメソッド名のいずれかに対応する word クイック ヒントが表示されます。 QuickInfo コント ローラーは、クイック ヒントのセッションをトリガーする、マウス ホバー イベント ハンドラーを実装します。  
  
#### <a name="to-implement-a-quickinfo-controller"></a>QuickInfo コント ローラーを実装するには  
  
1.  実装するクラスを宣言<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>、名前を付けます`TestQuickInfoController`します。  
  
     [!code-csharp[VSSDKQuickInfoTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#10)]
     [!code-vb[VSSDKQuickInfoTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#10)]  
  
2.  テキスト ビュー、QuickInfo セッション、およびクイック ヒントのコント ローラーのプロバイダーで表されるテキスト バッファーのテキスト ビューで、プライベート フィールドを追加します。  
  
     [!code-csharp[VSSDKQuickInfoTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#11)]
     [!code-vb[VSSDKQuickInfoTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#11)]  
  
3.  フィールドを設定し、マウス ホバー イベント ハンドラーを追加するコンス トラクターを追加します。  
  
     [!code-csharp[VSSDKQuickInfoTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#12)]
     [!code-vb[VSSDKQuickInfoTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#12)]  
  
4.  QuickInfo セッションをトリガーするマウス ホバー イベント ハンドラーを追加します。  
  
     [!code-csharp[VSSDKQuickInfoTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#13)]
     [!code-vb[VSSDKQuickInfoTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#13)]  
  
5.  実装、<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A>メソッドをコント ローラーが、テキスト ビューからデタッチされると、マウス ホバー イベント ハンドラーを削除します。  
  
     [!code-csharp[VSSDKQuickInfoTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#14)]
     [!code-vb[VSSDKQuickInfoTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#14)]  
  
6.  実装、<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A>メソッドと<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A>この例では空のメソッドとしてメソッド。  
  
     [!code-csharp[VSSDKQuickInfoTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#15)]
     [!code-vb[VSSDKQuickInfoTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#15)]  
  
## <a name="implementing-the-quickinfo-controller-provider"></a>QuickInfo コント ローラーのプロバイダーを実装します。  
 QuickInfo コント ローラーのプロバイダー自体を MEF コンポーネントの一部としてエクスポートおよび QuickInfo コント ローラーをインスタンス化する主な役割を果たします。 MEF コンポーネントの一部であるために、他の MEF コンポーネント パーツをインポートできます。  
  
#### <a name="to-implement-the-quickinfo-controller-provider"></a>QuickInfo コント ローラーのプロバイダーを実装するには  
  
1.  という名前のクラスを宣言`TestQuickInfoControllerProvider`を実装する<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>でエクスポートし、 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> 「ツールヒント QuickInfo コント ローラー」の<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>"text"。  
  
     [!code-csharp[VSSDKQuickInfoTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#16)]
     [!code-vb[VSSDKQuickInfoTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#16)]  
  
2.  <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> をプロパティとしてインポートします。  
  
     [!code-csharp[VSSDKQuickInfoTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#17)]
     [!code-vb[VSSDKQuickInfoTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#17)]  
  
3.  実装、 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> QuickInfo コント ローラーをインスタンス化するメソッド。  
  
     [!code-csharp[VSSDKQuickInfoTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#18)]
     [!code-vb[VSSDKQuickInfoTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#18)]  
  
## <a name="building-and-testing-the-code"></a>コードのビルドとテスト  
 このコードをテストするには、QuickInfoTest ソリューションをビルドし、実験用インスタンスで実行します。  
  
#### <a name="to-build-and-test-the-quickinfotest-solution"></a>ビルドして QuickInfoTest ソリューションをテストするには  
  
1.  ソリューションをビルドします。  
  
2.  デバッガーでこのプロジェクトを実行すると、Visual Studio の 2 つ目のインスタンスがインスタンス化されます。  
  
3.  テキスト ファイルと型がいくつかのテキストの単語を含む"add"および「減算」を作成します。  
  
4.  「追加」の出現回数の 1 つにマウス ポインターを移動します。 署名との説明、`add`メソッドを表示する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: コンテンツの種類とファイル名拡張子とをリンクさせる](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

