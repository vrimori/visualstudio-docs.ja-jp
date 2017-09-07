---
title: "チュートリアル: クイック ツールヒントの表示 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
caps.latest.revision: 27
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
ms.translationtype: MT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 7acb244077949ffb0a59018b24706fd3ccfefc14
ms.contentlocale: ja-jp
ms.lasthandoff: 09/06/2017

---
# <a name="walkthrough-displaying-quickinfo-tooltips"></a>チュートリアル: クイック ツールヒントの表示
QuickInfo はメソッドのシグネチャを表示する IntelliSense 機能である場合、ユーザーの説明が、ポインターをメソッド名の上に移動します。 QuickInfo の説明を提供する識別子を定義して、コンテンツを表示するツールヒントを作成して QuickInfo などの機能の言語に基づくを実装できます。 QuickInfo を定義するには、言語サービスのコンテキストで独自ファイル名拡張子とコンテンツの種類を定義してその種類のクィック ヒントを表示またはクイック ヒントを表示するには、既存のコンテンツの種類 ("text") などの。 このチュートリアルでは、"text"コンテンツ タイプのクィック ヒントを表示する方法を示します。  
  
 このチュートリアルで QuickInfo 例は、ユーザーがメソッド名の上、ポインターを移動したときに、ツールヒントを表示します。 この設計では、これら 4 つのインターフェイスを実装する必要があります。  
  
-   ソース インターフェイス  
  
-   ソース プロバイダー インターフェイス  
  
-   コント ローラーのインターフェイス  
  
-   コント ローラー プロバイダー インターフェイス  
  
 ソースとコント ローラーのプロバイダーは、Managed Extensibility Framework (MEF) コンポーネントの部分、ソースとコント ローラー クラスをエクスポートするのには、インポートするサービス ブローカーなど、<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>ツールヒントのテキストを作成します。バッファー、および<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>、QuickInfo セッションをトリガーします。  
  
 この例では QuickInfo ソース リストを使用するハード コーディングされたメソッドの名前と説明については、が、完全な実装で、言語サービスと言語のドキュメントがそのコンテンツを提供することを担当します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降で、ダウンロード センターから、Visual Studio SDK をインストールするはできません。 Visual Studio のセットアップのオプション機能として含まれます。 後でまた VS SDK をインストールすることができます。 詳細については、次を参照してください。 [、Visual Studio SDK をインストールする](../extensibility/installing-the-visual-studio-sdk.md)です。  
  
## <a name="creating-a-mef-project"></a>MEF プロジェクトを作成します。  
  
#### <a name="to-create-a-mef-project"></a>MEF プロジェクトを作成するには  
  
1.  C# の場合は、VSIX プロジェクトを作成します。 (で、**新しいプロジェクト**ダイアログで、 **Visual c#/機能拡張**、し**VSIX プロジェクト**)。ソリューションの名前を付けます`QuickInfoTest`です。  
  
2.  エディター分類子項目テンプレートをプロジェクトに追加します。 詳細については、次を参照してください。[エディター項目テンプレートに、拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)です。  
  
3.  既存のクラス ファイルを削除します。  
  
## <a name="implementing-the-quickinfo-source"></a>QuickInfo ソースの実装  
 QuickInfo ソースは、識別子とその説明のセットを収集し、識別子のいずれかが発生したときにツールヒントのテキスト バッファーへのコンテンツの追加を担当します。 この例では、識別子とその説明はで追加ソース コンス トラクターです。  
  
#### <a name="to-implement-the-quickinfo-source"></a>QuickInfo ソースを実装するには  
  
1.  クラス ファイルを追加し、名前を付けます`TestQuickInfoSource`です。  
  
2.  Microsoft.VisualStudio.Language.IntelliSense への参照を追加します。  
  
3.  次の imports を追加します。  
  
     [!code-vb[VSSDKQuickInfoTest 1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb)][!code-csharp[VSSDKQuickInfoTest 1  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]  
  
4.  実装するクラスを宣言<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>、名前を付けます`TestQuickInfoSource`です。  
  
     [!code-vb[VSSDKQuickInfoTest 2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb)][!code-csharp[VSSDKQuickInfoTest 2  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]  
  
5.  テキスト バッファーと一連のメソッド名とメソッドのシグネチャでは、QuickInfo ソース プロバイダーのフィールドを追加します。 この例でメソッドの名前とシグネチャを初期化します。、`TestQuickInfoSource`コンス トラクターです。  
  
     [!code-vb[VSSDKQuickInfoTest 3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb)][!code-csharp[VSSDKQuickInfoTest 3  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]  
  
6.  QuickInfo ソース プロバイダーとテキスト バッファーを設定し、メソッド名、およびメソッドのシグネチャと説明のセットを設定するコンス トラクターを追加します。  
  
     [!code-vb[VSSDKQuickInfoTest 4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb)][!code-csharp[VSSDKQuickInfoTest 4  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]  
  
7.  <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A> メソッドを実装します。 この例では、メソッドを検索、現在の単語または前の単語、またはテキスト バッファーの行の最後のカーソルがある場合。 単語が、メソッド名のいずれかの場合は、そのメソッド名の説明が QuickInfo コンテンツに追加されます。  
  
     [!code-vb[VSSDKQuickInfoTest 5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb)][!code-csharp[VSSDKQuickInfoTest #5  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]  
  
8.  以降、Dispose() メソッドを実装することも必要があります<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>実装<xref:System.IDisposable>:。  
  
     [!code-vb[VSSDKQuickInfoTest 6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb)][!code-csharp[VSSDKQuickInfoTest 6  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]  
  
## <a name="implementing-a-quickinfo-source-provider"></a>QuickInfo ソース プロバイダーを実装します。  
 QuickInfo ソースのプロバイダーは、MEF コンポーネント パーツとして自体をエクスポートおよび QuickInfo ソースをインスタンス化する、主に機能します。 MEF コンポーネント パーツになっているために、他の MEF コンポーネント パーツをインポートできます。  
  
#### <a name="to-implement-a-quickinfo-source-provider"></a>QuickInfo ソース プロバイダーを実装するには  
  
1.  という名前の QuickInfo ソース プロバイダーを宣言`TestQuickInfoSourceProvider`を実装する<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>、およびエクスポートに、 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "ツールヒント QuickInfo Source"の<xref:Microsoft.VisualStudio.Utilities.OrderAttribute>の Before ="default"、および<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>"text"のです。  
  
     [!code-vb[VSSDKQuickInfoTest 7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb)][!code-csharp[VSSDKQuickInfoTest 7  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]  
  
2.  2 つのエディター サービスをインポート<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>と<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>のプロパティとして`TestQuickInfoSourceProvider`です。  
  
     [!code-vb[VSSDKQuickInfoTest 8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb)][!code-csharp[VSSDKQuickInfoTest 8  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]  
  
3.  実装<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A>を返す新しい`TestQuickInfoSource`です。  
  
     [!code-vb[VSSDKQuickInfoTest 9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb)][!code-csharp[VSSDKQuickInfoTest 9  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]  
  
## <a name="implementing-a-quickinfo-controller"></a>QuickInfo コント ローラーの実装  
 QuickInfo コント ローラーは、クイック ヒントを表示するかを決定します。 この例では、ポインターが、メソッド名のいずれかに対応する word QuickInfo が表示されます。 QuickInfo コント ローラーでは、QuickInfo セッションをトリガーする、マウス ホバー イベント ハンドラーを実装します。  
  
#### <a name="to-implement-a-quickinfo-controller"></a>QuickInfo コント ローラーを実装するには  
  
1.  実装するクラスを宣言<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>、名前を付けます`TestQuickInfoController`です。  
  
     [!code-vb[VSSDKQuickInfoTest 10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb)][!code-csharp[VSSDKQuickInfoTest 10  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]  
  
2.  テキスト ビューのプライベート フィールドをテキスト ビュー、QuickInfo セッションおよび QuickInfo コント ローラーのプロバイダーで表されるテキスト バッファーを追加します。  
  
     [!code-vb[VSSDKQuickInfoTest #11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb)][!code-csharp[VSSDKQuickInfoTest #11  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]  
  
3.  フィールドを設定し、マウス ホバー イベント ハンドラーを追加するコンス トラクターを追加します。  
  
     [!code-vb[VSSDKQuickInfoTest #12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb)][!code-csharp[VSSDKQuickInfoTest #12  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]  
  
4.  QuickInfo セッションをトリガーする、マウス ホバー イベント ハンドラーを追加します。  
  
     [!code-vb[VSSDKQuickInfoTest #13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb)][!code-csharp[VSSDKQuickInfoTest #13  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]  
  
5.  実装、<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A>メソッドため、コント ローラーがテキスト ビューからデタッチされると、it がマウス ホバー イベント ハンドラーを削除のします。  
  
     [!code-vb[VSSDKQuickInfoTest #14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb)][!code-csharp[VSSDKQuickInfoTest #14  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]  
  
6.  実装、<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A>メソッドおよび<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A>この例の空のメソッドとしてメソッドです。  
  
     [!code-vb[VSSDKQuickInfoTest #15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb)][!code-csharp[VSSDKQuickInfoTest #15  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]  
  
## <a name="implementing-the-quickinfo-controller-provider"></a>QuickInfo コント ローラーのプロバイダーの実装  
 QuickInfo コント ローラーのプロバイダーは、MEF コンポーネント パーツとして自体をエクスポートおよび QuickInfo コント ローラーをインスタンス化する、主に機能します。 MEF コンポーネント パーツになっているために、他の MEF コンポーネント パーツをインポートできます。  
  
#### <a name="to-implement-the-quickinfo-controller-provider"></a>QuickInfo コント ローラーのプロバイダーを実装するには  
  
1.  という名前のクラスを宣言`TestQuickInfoControllerProvider`を実装する<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>、およびエクスポートして、 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "ツールヒント QuickInfo Controller"のおよび<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>"text"。  
  
     [!code-vb[VSSDKQuickInfoTest #16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb)][!code-csharp[VSSDKQuickInfoTest #16  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]  
  
2.  インポート、<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>プロパティとして。  
  
     [!code-vb[VSSDKQuickInfoTest 17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb)][!code-csharp[VSSDKQuickInfoTest 17  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]  
  
3.  実装、 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> QuickInfo コント ローラーをインスタンス化する方法です。  
  
     [!code-vb[VSSDKQuickInfoTest #18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb)][!code-csharp[VSSDKQuickInfoTest #18  ](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]  
  
## <a name="building-and-testing-the-code"></a>コードのビルドとテスト  
 このコードをテストするには、QuickInfoTest ソリューションをビルドし、実験用インスタンスで実行します。  
  
#### <a name="to-build-and-test-the-quickinfotest-solution"></a>ビルドし、QuickInfoTest ソリューションをテストするには  
  
1.  ソリューションをビルドします。  
  
2.  デバッガーでこのプロジェクトを実行すると、Visual Studio の 2 つ目のインスタンスがインスタンス化されます。  
  
3.  テキスト ファイルと、単語を含むいくつかのテキストを「追加」の種類、および「減算」を作成します。  
  
4.  ポインターは、「追加」の出現回数は、のいずれかの上に移動します。 署名との説明、`add`メソッドを表示する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: コンテンツの種類とファイル名拡張子とをリンクさせる](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
