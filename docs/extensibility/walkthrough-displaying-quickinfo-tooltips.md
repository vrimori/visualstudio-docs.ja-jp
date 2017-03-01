---
title: "チュートリアル: クイック ヒントの表示 |Microsoft ドキュメント"
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: b533e77a2310194b2bccc225f9902e5a8d502da5
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-displaying-quickinfo-tooltips"></a>チュートリアル: クイック ヒントの表示
クイック ヒントはメソッドのシグネチャを表示する IntelliSense 機能であり説明と、ユーザーがポインターをメソッド名の上に移動します。 クイック ヒントなどの機能の言語をベースとは、クイック ヒントの説明を提供する識別子を定義して、コンテンツを表示するツールヒントを作成して実装できます。 クイック ヒントを定義するには、言語サービスのコンテキストで独自ファイル名拡張子とコンテンツ タイプを定義し、その型だけのクイック ヒントを表示できます。 または"text") などの既存のコンテンツ タイプのクイック ヒントを表示することができます。 このチュートリアルでは、"text"コンテンツ タイプのクイック ヒントを表示する方法を示します。  
  
 クイック ヒントの使用例このチュートリアルでは、ユーザーは、メソッド名の上、ポインターを移動すると、ツールヒントを表示します。 この設計では、これら&4; つのインターフェイスを実装する必要があります。  
  
-   送信元インターフェイス  
  
-   ソースのプロバイダー インターフェイス  
  
-   コント ローラーのインターフェイス  
  
-   コント ローラーのプロバイダー インターフェイス  
  
 ソースとコント ローラーのプロバイダーは、Managed Extensibility Framework (MEF) コンポーネントの部分を担当しています、ソースおよびコント ローラー クラスをエクスポートしてをインポートするサービス ブローカーなど、 <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>、ツールヒントのテキスト バッファーを作成して、 <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>、クイック ヒントのセッションをトリガーする</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker></xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>。  
  
 この例でクイック ヒントのソースには、メソッドの名前と説明については、ハードコーディングされたリストが使用されているが、完全な実装で言語サービスと language のドキュメントは、そのコンテンツを提供します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。 詳細については、次を参照してください。 [Visual Studio SDK をインストールする](../extensibility/installing-the-visual-studio-sdk.md)です。  
  
## <a name="creating-a-mef-project"></a>MEF プロジェクトを作成します。  
  
#### <a name="to-create-a-mef-project"></a>MEF プロジェクトを作成するには  
  
1.  C# の場合は、VSIX プロジェクトを作成します。 (で、**新しいプロジェクト**ダイアログで、 **Visual c#/機能拡張**、し**VSIX プロジェクト**)。ソリューションの名前`QuickInfoTest`します。  
  
2.  エディターの分類子の項目テンプレートをプロジェクトに追加します。 詳細については、次を参照してください。[エディター項目テンプレートを使用して拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)します。  
  
3.  既存のクラス ファイルを削除します。  
  
## <a name="implementing-the-quickinfo-source"></a>クイック ヒントのソースの実装  
 クイック ヒントのソースは、識別子とその説明のセットを収集し、識別子のいずれかが発生したときに、ツールヒントのテキスト バッファーに、コンテンツを追加します。 この例ではソース コンス トラクターに、識別子とその説明はだけ追加できます。  
  
#### <a name="to-implement-the-quickinfo-source"></a>クイック ヒントのソースを実装するには  
  
1.  クラス ファイルを追加し、名前`TestQuickInfoSource`します。  
  
2.  Microsoft.VisualStudio.Language.IntelliSense への参照を追加します。  
  
3.  次の imports を追加します。  
  
     [!code-vb[VSSDKQuickInfoTest&1;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&1;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]  
  
4.  実装するクラスを宣言<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>と名付けます`TestQuickInfoSource`</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>。  
  
     [!code-vb[VSSDKQuickInfoTest&2;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&2;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]  
  
5.  クイック ヒント ソース プロバイダー、テキスト バッファーと、一連のメソッド名とメソッドのシグネチャのフィールドを追加します。 この例でメソッドの名前とシグニチャを初期化します。、`TestQuickInfoSource`コンス トラクターです。  
  
     [!code-vb[VSSDKQuickInfoTest&3;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&3;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]  
  
6.  クイック同期元プロバイダーとテキスト バッファーを設定し、メソッド名、およびメソッドのシグネチャと説明のセットを設定するコンス トラクターを追加します。  
  
     [!code-vb[VSSDKQuickInfoTest&4;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&4;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]  
  
7.  実装、<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A>メソッド</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A>。 この例では、メソッドが検出した現在の単語または前の単語、カーソルが行またはテキスト バッファーの末尾にある場合。 単語がメソッド名のいずれかの場合は、クイック ヒントのコンテンツに対応するメソッド名の説明が追加されます。  
  
     [!code-vb[VSSDKQuickInfoTest&5;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&5;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]  
  
8.  <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> <xref:System.IDisposable>::</xref:System.IDisposable>を実装する</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>ための Dispose() メソッドを実装することも必要があります。  
  
     [!code-vb[VSSDKQuickInfoTest&6;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&6;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]  
  
## <a name="implementing-a-quickinfo-source-provider"></a>クイック ヒント ソース プロバイダーを実装します。  
 クイック ヒントのソースのプロバイダーでは、主に自体を MEF コンポーネントの一部としてエクスポートし、クイック ヒントのソースをインスタンス化されます。 MEF コンポーネントの一部であるために、他の MEF コンポーネント パーツをインポートできます。  
  
#### <a name="to-implement-a-quickinfo-source-provider"></a>クイック ヒント ソース プロバイダーを実装するには  
  
1.  という名前のクイック ヒント ソース プロバイダーを宣言`TestQuickInfoSourceProvider`を実装する<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>、およびエクスポートして、 <xref:Microsoft.VisualStudio.Utilities.NameAttribute>"ツールヒント QuickInfo Source"の<xref:Microsoft.VisualStudio.Utilities.OrderAttribute>の前に"default"を = と<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>"text"の</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute></xref:Microsoft.VisualStudio.Utilities.OrderAttribute></xref:Microsoft.VisualStudio.Utilities.NameAttribute></xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>。  
  
     [!code-vb[VSSDKQuickInfoTest&7;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&7;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]  
  
2.  2 つのエディター サービスをインポート<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>と<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>のプロパティとして`TestQuickInfoSourceProvider`</xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService></xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>。  
  
     [!code-vb[VSSDKQuickInfoTest&8;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&8;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]  
  
3.  実装<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A>を返す新しい`TestQuickInfoSource`</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A>。  
  
     [!code-vb[9 番目の VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&9;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]  
  
## <a name="implementing-a-quickinfo-controller"></a>クイック ヒントのコント ローラーの実装  
 クイック ヒントのコント ローラーは、クイック ヒントを表示するかを決定します。 この例では、ポインターがメソッド名のいずれかに対応する単語の上にあるとき、クイック ヒントが表示されます。 クイック ヒントのコント ローラーでは、クイック ヒントのセッションをトリガーする、マウス ホバー イベント ハンドラーを実装します。  
  
#### <a name="to-implement-a-quickinfo-controller"></a>クイック ヒントのコント ローラーを実装するには  
  
1.  実装するクラスを宣言<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>と名付けます`TestQuickInfoController`</xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>。  
  
     [!code-vb[VSSDKQuickInfoTest&#10;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#10;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]  
  
2.  テキスト ビュー、クイック ヒント セッションおよびクイック ヒントのコント ローラーのプロバイダーで表されるテキスト バッファー テキスト ビューのプライベート フィールドを追加します。  
  
     [!code-vb[VSSDKQuickInfoTest&#11;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#11;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]  
  
3.  フィールドを設定し、マウス ホバー イベント ハンドラーを追加するコンス トラクターを追加します。  
  
     [!code-vb[VSSDKQuickInfoTest&#12;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#12;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]  
  
4.  クイック ヒントのセッションをトリガーするマウス ホバー イベント ハンドラーを追加します。  
  
     [!code-vb[VSSDKQuickInfoTest&#13;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#13;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]  
  
5.  実装、<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A>メソッドのため、it がテキスト ビューから、コント ローラーがデタッチされると、マウス ホバー イベント ハンドラーを削除します</xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A>。  
  
     [!code-vb[VSSDKQuickInfoTest&#14;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#14;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]  
  
6.  実装、<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A>メソッドおよび<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A>この例については、空のメソッドとしてメソッド</xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A></xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A>。  
  
     [!code-vb[VSSDKQuickInfoTest&#15;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#15;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]  
  
## <a name="implementing-the-quickinfo-controller-provider"></a>クイック ヒントのコント ローラーのプロバイダーを実装します。  
 クイック ヒントのコント ローラーのプロバイダー自体を MEF コンポーネントの一部としてエクスポートし、クイック ヒントのコント ローラーをインスタンス化する主な役割を果たします。 MEF コンポーネントの一部であるために、他の MEF コンポーネント パーツをインポートできます。  
  
#### <a name="to-implement-the-quickinfo-controller-provider"></a>クイック ヒントのコント ローラーのプロバイダーを実装するには  
  
1.  という名前のクラスを宣言`TestQuickInfoControllerProvider`を実装する<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>、およびエクスポートして、 <xref:Microsoft.VisualStudio.Utilities.NameAttribute>「ツールヒント クイック ヒントのコント ローラー」の<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>"text"の:</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> </xref:Microsoft.VisualStudio.Utilities.NameAttribute> </xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>  
  
     [!code-vb[VSSDKQuickInfoTest&#16;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#16;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]  
  
2.  インポート、<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>プロパティとして</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>。  
  
     [!code-vb[VSSDKQuickInfoTest&17;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&17;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]  
  
3.  実装、 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A>QuickInfo コント ローラーをインスタンス化するメソッド</xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A>。  
  
     [!code-vb[VSSDKQuickInfoTest&18;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&18;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]  
  
## <a name="building-and-testing-the-code"></a>コードのビルドとテスト  
 このコードをテストするには、QuickInfoTest ソリューションをビルドし、実験用インスタンスで実行します。  
  
#### <a name="to-build-and-test-the-quickinfotest-solution"></a>ビルドし、QuickInfoTest ソリューションをテストするには  
  
1.  ソリューションをビルドします。  
  
2.  デバッガーでこのプロジェクトを実行すると、Visual Studio の&2; つ目のインスタンスがインスタンス化されます。  
  
3.  テキスト ファイルと型の文字列が含まれたテキストを「追加」と「減算」を作成します。  
  
4.  "Add"の出現回数の&1; つに、ポインターを移動します。 説明と、署名、`add`メソッドを表示する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: ファイル名拡張子へのコンテンツの種類のリンク](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
