---
title: 'チュートリアル: スマート タグの表示 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - smart tags
ms.assetid: 10bb4f69-b259-41f0-b91a-69b04385d9a5
caps.latest.revision: 31
manager: douge
ms.openlocfilehash: 15e02986012f186ce4bcb2fdcd6914396b2b597e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47544951"
---
# <a name="walkthrough-displaying-smarttags"></a>チュートリアル: スマート タグの表示
スマート タグは非推奨とされており、代わって電球が使用されるようになりました。 参照してください[チュートリアル: Displaying Light Bulb Suggestions](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)します。  
  
 スマート タグは、一連の操作を表示するために展開されるテキスト上のタグです。 たとえば、Visual Basic や Visual C# のプロジェクトでは、変数名などの識別子の名前を変更すると、赤い線が単語の下に表示されます。 下線の上にポインターを移動すると、ポインターの近くにボタンが表示されます。 ボタンをクリックすると、 **"IsRead の名前を IsReady に変更する"** などの、提案されるアクションが表示されます。 操作をクリックすると、プロジェクトでの **IsRead** へのすべての参照が **IsReady**という名前に変更されます。  
  
 サブクラス化してスマート タグを実装するにはスマート タグには、エディターの IntelliSense 実装の一部が、<xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag>を実装して、<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>インターフェイスと<xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>インターフェイス。  
  
> [!NOTE]
>  その他のタグも、同様の方法で実装できます。  
  
 次のチュートリアルでは、現在の単語の上に表示され、 **Convert to upper case** と **Convert to lower case**の 2 つのアクションを提案するスマート タグを作成する方法を示します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルに従うには、Visual Studio SDK をインストールする必要があります。 詳細については、次を参照してください。 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)します。  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF) プロジェクトの作成  
  
#### <a name="to-create-a-mef-project"></a>MEF プロジェクトを作成するには  
  
1.  エディター分類子プロジェクトを作成します。 ソリューション `SmartTagTest`の名前を指定します。  
  
2.  VSIX マニフェスト エディターで source.extension.vsixmanifest ファイルを開きます。  
  
3.  **資産** セクションに `Microsoft.VisualStudio.MefComponent` 型が含まれ、 **ソース** が `A project in current solution`に設定され、 **プロジェクト** が SmartTagTest.dll に設定されていることを確認します。  
  
4.  source.extension.vsixmanifest を保存して閉じます。  
  
5.  プロジェクトに次の参照を追加し、 **CopyLocal** を `false`に設定します。  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
6.  既存のクラス ファイルを削除します。  
  
## <a name="implementing-a-tagger-for-smart-tags"></a>スマート タグのタガーの実装  
  
#### <a name="to-implement-a-tagger-for-smart-tags"></a>スマート タグのタガーを実装するには  
  
1.  クラス ファイルを追加し、その名前を `TestSmartTag`にします。  
  
2.  次のインポートを追加します。  
  
     [!code-csharp[VSSDKSmartTagTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#1)]
     [!code-vb[VSSDKSmartTagTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#1)]  
  
3.  という名前のクラスを追加`TestSmartTag`から継承する<xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag>します。  
  
     [!code-csharp[VSSDKSmartTagTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#2)]
     [!code-vb[VSSDKSmartTagTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#2)]  
  
4.  このクラスで基底コンス トラクターを呼び出すコンス トラクターを追加、<xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType>の<xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType>単語の最初の文字の下に表示される青い線が発生します。 (を使用する場合<xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType>、赤い線は、最後の文字の単語の下に表示されます)。  
  
     [!code-csharp[VSSDKSmartTagTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#3)]
     [!code-vb[VSSDKSmartTagTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#3)]  
  
5.  という名前のクラスを追加`TestSmartTagger`から継承する<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>型の`TestSmartTag`、実装と<xref:System.IDisposable>します。  
  
     [!code-csharp[VSSDKSmartTagTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#4)]
     [!code-vb[VSSDKSmartTagTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#4)]  
  
6.  タガー クラスに次のプライベート フィールドを追加します。  
  
     [!code-csharp[VSSDKSmartTagTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#5)]
     [!code-vb[VSSDKSmartTagTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#5)]  
  
7.  プライベート フィールドを設定し、サブスクライブするコンス トラクターを追加、<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>イベント。  
  
     [!code-csharp[VSSDKSmartTagTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#6)]
     [!code-vb[VSSDKSmartTagTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#6)]  
  
8.  実装<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>現在の単語のタグが作成されるようにします。 (このメソッドは、後述するプライベート メソッド `GetSmartTagActions` も呼び出します)。  
  
     [!code-csharp[VSSDKSmartTagTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#7)]
     [!code-vb[VSSDKSmartTagTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#7)]  
  
9. スマート タグ操作を設定するメソッド `GetSmartTagActions` を追加します。 操作自体は、後の手順で実装します。  
  
     [!code-csharp[VSSDKSmartTagTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#8)]
     [!code-vb[VSSDKSmartTagTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#8)]  
  
10. `SmartTagsChanged` イベントを宣言します。  
  
     [!code-csharp[VSSDKSmartTagTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#9)]
     [!code-vb[VSSDKSmartTagTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#9)]  
  
11. 実装、`OnLayoutChanged`発生するイベント ハンドラー、`TagsChanged`イベント、<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>呼び出されます。  
  
     [!code-csharp[VSSDKSmartTagTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#10)]
     [!code-vb[VSSDKSmartTagTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#10)]  
  
12. 実装、<xref:System.IDisposable.Dispose%2A>購読を中止するためのメソッド、<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>イベント。  
  
     [!code-csharp[VSSDKSmartTagTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#11)]
     [!code-vb[VSSDKSmartTagTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#11)]  
  
## <a name="implementing-the-smart-tag-tagger-provider"></a>スマート タグ タガー プロバイダーの実装  
  
#### <a name="to-implement-the-smart-tag-tagger-provider"></a>スマート タグ タガー プロバイダーを実装するには  
  
1.  という名前のクラスを追加`TestSmartTagTaggerProvider`から継承する<xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>します。 エクスポートすると、 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text"の<xref:Microsoft.VisualStudio.Utilities.OrderAttribute>の Before ="default"と<xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>の<xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag>。  
  
     [!code-csharp[VSSDKSmartTagTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#12)]
     [!code-vb[VSSDKSmartTagTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#12)]  
  
2.  インポート、<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>プロパティとして。  
  
     [!code-csharp[VSSDKSmartTagTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#13)]
     [!code-vb[VSSDKSmartTagTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#13)]  
  
3.  <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> メソッドを実装します。  
  
     [!code-csharp[VSSDKSmartTagTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#14)]
     [!code-vb[VSSDKSmartTagTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#14)]  
  
## <a name="implementing-smart-tag-actions"></a>スマート タグ操作の実装  
  
#### <a name="to-implement-smart-tag-actions"></a>スマート タグ操作を実装するには  
  
1.  2 つのクラスを、1 つは `UpperCaseSmartTagAction` という名前で、もう 1 つは `LowerCaseSmartTagAction`という名前で作成します。 これらのクラスは、どちらも <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction> を実装しています。  
  
     [!code-csharp[VSSDKSmartTagTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#15)]
     [!code-vb[VSSDKSmartTagTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#15)]  
  
     [!code-csharp[VSSDKSmartTagTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#16)]
     [!code-vb[VSSDKSmartTagTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#16)]  
  
 両方のクラスは似ていますが呼び出される<xref:System.String.ToUpper%2A>およびその他の呼び出し<xref:System.String.ToLower%2A>します。 次の手順では大文字操作クラスのみを対象にしていますが、両方のクラスを実装する必要があります。 小文字操作を実装するためのパターンとして、大文字操作を実装するための手順を使用します。  
  
1.  一連のプライベート フィールドを宣言します。  
  
     [!code-csharp[VSSDKSmartTagTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#17)]
     [!code-vb[VSSDKSmartTagTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#17)]  
  
2.  フィールドを設定するコンストラクターを追加します。  
  
     [!code-csharp[VSSDKSmartTagTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#18)]
     [!code-vb[VSSDKSmartTagTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#18)]  
  
3.  次のようにプロパティを設定します。  
  
     [!code-csharp[VSSDKSmartTagTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#19)]
     [!code-vb[VSSDKSmartTagTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#19)]  
  
4.  実装、<xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction.Invoke%2A>範囲内のテキストを等価な大文字に置き換えることによりメソッド。  
  
     [!code-csharp[VSSDKSmartTagTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#20)]
     [!code-vb[VSSDKSmartTagTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#20)]  
  
## <a name="building-and-testing-the-code"></a>コードのビルドとテスト  
 このコードをテストするには、SmartTagTest ソリューションをビルドし、実験用インスタンスで実行します。  
  
#### <a name="to-build-and-test-the-smarttagtest-solution"></a>SmartTagTest ソリューションをビルドし、テストするには  
  
1.  ソリューションをビルドします。  
  
2.  デバッガーでこのプロジェクトを実行すると、Visual Studio の 2 つ目のインスタンスがインスタンス化されます。  
  
3.  テキスト ファイルを作成し、いくつかのテキストを入力します。  
  
     テキストの最初の単語の最初の文字の下に青い線が表示されます。  
  
4.  青い線の上にポインターを移動します。  
  
     ポインターの近くにボタンが表示されます。  
  
5.  ボタンをクリックすると、 **Convert to upper case** と **Convert to lower case**という 2 つの提案されるアクションが表示されます。 最初の操作をクリックすると、現在の単語内のすべてのテキストが大文字に変換されます。 2 つ目の操作をクリックすると、すべてのテキストが小文字に変換されます。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: コンテンツの種類とファイル名拡張子とをリンクさせる](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)