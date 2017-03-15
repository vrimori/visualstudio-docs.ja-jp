---
title: "チュートリアル: スマート タグの表示 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK]、新規 - スマート タグ"
ms.assetid: 10bb4f69-b259-41f0-b91a-69b04385d9a5
caps.latest.revision: 31
caps.handback.revision: 31
manager: "douge"
---
# チュートリアル: スマート タグの表示
スマート タグは廃止され、代わって電球が使用されるようになりました。 「[チュートリアル: 電球検索候補の表示](../Topic/Walkthrough:%20Displaying%20Light%20Bulb%20Suggestions.md)」を参照してください。  
  
 スマート タグは、一連の操作を表示するために展開されるテキスト上のタグです。 たとえば、Visual Basic や Visual C\# のプロジェクトでは、変数名などの識別子の名前を変更すると、赤い線が単語の下に表示されます。 下線の上にポインターを移動すると、ポインターの近くにボタンが表示されます。 ボタンをクリックすると、**"IsRead の名前を IsReady に変更する"** などの、提案されるアクションが表示されます。 操作をクリックすると、プロジェクトでの **IsRead** へのすべての参照が **IsReady** という名前に変更されます。  
  
 スマート タグはエディターの IntelliSense 実装の一部ですが、<xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag> をサブクラス化してから <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> インターフェイスおよび <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> インターフェイスを実装することで、スマート タグを実装できます。  
  
> [!NOTE]
>  その他のタグも、同様の方法で実装できます。  
  
 次のチュートリアルでは、現在の単語の上に表示され、**Convert to upper case** と **Convert to lower case** の 2 つのアクションを提案するスマート タグを作成する方法を示します。  
  
## 必須コンポーネント  
 このチュートリアルに従うには、Visual Studio SDK をインストールする必要があります。 詳細については、「[Visual Studio SDK](../extensibility/visual-studio-sdk.md)」を参照してください。  
  
## Managed Extensibility Framework \(MEF\) プロジェクトの作成  
  
#### MEF プロジェクトを作成するには  
  
1.  エディター分類子プロジェクトを作成します。 ソリューション `SmartTagTest` の名前を指定します。  
  
2.  VSIX マニフェスト エディターで source.extension.vsixmanifest ファイルを開きます。  
  
3.  **資産** セクションに `Microsoft.VisualStudio.MefComponent` 型が含まれ、**ソース** が `A project in current solution` に設定され、**プロジェクト** が SmartTagTest.dll に設定されていることを確認します。  
  
4.  source.extension.vsixmanifest を保存して閉じます。  
  
5.  プロジェクトに次の参照を追加し、**CopyLocal** を `false` に設定します。  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
6.  既存のクラス ファイルを削除します。  
  
## スマート タグのタガーの実装  
  
#### スマート タグのタガーを実装するには  
  
1.  クラス ファイルを追加し、その名前を `TestSmartTag` にします。  
  
2.  次のインポートを追加します。  
  
     [!code-cs[VSSDKSmartTagTest#1](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_1.cs)]
     [!code-vb[VSSDKSmartTagTest#1](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_1.vb)]  
  
3.  <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag> から継承するクラスを `TestSmartTag` という名前で追加します。  
  
     [!code-cs[VSSDKSmartTagTest#2](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_2.cs)]
     [!code-vb[VSSDKSmartTagTest#2](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_2.vb)]  
  
4.  <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType> の <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType> で基底コンストラクターを呼び出す、このクラスのコンストラクターを追加します。これにより、単語の最初の文字の下に青い線が表示されます \(<xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType> を使用すると、単語の最後の文字の下に赤い線が表示されます\)。  
  
     [!code-cs[VSSDKSmartTagTest#3](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_3.cs)]
     [!code-vb[VSSDKSmartTagTest#3](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_3.vb)]  
  
5.  型 `TestSmartTag` の <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> から継承し、<xref:System.IDisposable> を実装するクラスを `TestSmartTagger` という名前で追加します。  
  
     [!code-cs[VSSDKSmartTagTest#4](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_4.cs)]
     [!code-vb[VSSDKSmartTagTest#4](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_4.vb)]  
  
6.  タガー クラスに次のプライベート フィールドを追加します。  
  
     [!code-cs[VSSDKSmartTagTest#5](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_5.cs)]
     [!code-vb[VSSDKSmartTagTest#5](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_5.vb)]  
  
7.  プライベート フィールドを設定し、<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> イベントを購読するコンストラクターを追加します。  
  
     [!code-cs[VSSDKSmartTagTest#6](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_6.cs)]
     [!code-vb[VSSDKSmartTagTest#6](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_6.vb)]  
  
8.  現在の単語に対してタグが作成されるように <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> を実装します \(このメソッドは、後述するプライベート メソッド `GetSmartTagActions` も呼び出します\)。  
  
     [!code-cs[VSSDKSmartTagTest#7](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_7.cs)]
     [!code-vb[VSSDKSmartTagTest#7](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_7.vb)]  
  
9. スマート タグ操作を設定するメソッド `GetSmartTagActions` を追加します。 操作自体は、後の手順で実装します。  
  
     [!code-cs[VSSDKSmartTagTest#8](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_8.cs)]
     [!code-vb[VSSDKSmartTagTest#8](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_8.vb)]  
  
10. `SmartTagsChanged` イベントを宣言します。  
  
     [!code-cs[VSSDKSmartTagTest#9](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_9.cs)]
     [!code-vb[VSSDKSmartTagTest#9](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_9.vb)]  
  
11. `TagsChanged` イベントが発生して <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> が呼び出されるように、`OnLayoutChanged` イベント ハンドラーを実装します。  
  
     [!code-cs[VSSDKSmartTagTest#10](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_10.cs)]
     [!code-vb[VSSDKSmartTagTest#10](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_10.vb)]  
  
12. <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> イベントの購読を中止するようにメソッド <xref:System.IDisposable.Dispose%2A> を実装します。  
  
     [!code-cs[VSSDKSmartTagTest#11](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_11.cs)]
     [!code-vb[VSSDKSmartTagTest#11](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_11.vb)]  
  
## スマート タグ タガー プロバイダーの実装  
  
#### スマート タグ タガー プロバイダーを実装するには  
  
1.  <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> から継承するクラスを `TestSmartTagTaggerProvider` という名前で追加します。<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> を "text"、<xref:Microsoft.VisualStudio.Utilities.OrderAttribute> を Before\="default"、および <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> を <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag> にして、そのクラスをエクスポートします。  
  
     [!code-cs[VSSDKSmartTagTest#12](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_12.cs)]
     [!code-vb[VSSDKSmartTagTest#12](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_12.vb)]  
  
2.  <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> をプロパティとしてインポートします。  
  
     [!code-cs[VSSDKSmartTagTest#13](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_13.cs)]
     [!code-vb[VSSDKSmartTagTest#13](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_13.vb)]  
  
3.  <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> メソッドを実装します。  
  
     [!code-cs[VSSDKSmartTagTest#14](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_14.cs)]
     [!code-vb[VSSDKSmartTagTest#14](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_14.vb)]  
  
## スマート タグ操作の実装  
  
#### スマート タグ操作を実装するには  
  
1.  2 つのクラスを、1 つは `UpperCaseSmartTagAction` という名前で、もう 1 つは `LowerCaseSmartTagAction` という名前で作成します。 どちらのクラスも、<xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction> を実装します。  
  
     [!code-cs[VSSDKSmartTagTest#15](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_15.cs)]
     [!code-vb[VSSDKSmartTagTest#15](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_15.vb)]  
  
     [!code-cs[VSSDKSmartTagTest#16](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_16.cs)]
     [!code-vb[VSSDKSmartTagTest#16](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_16.vb)]  
  
 両クラスは似ていますが、一方は <xref:System.String.ToUpper%2A> を呼び出し、他方は <xref:System.String.ToLower%2A> を呼び出します。 次の手順では大文字操作クラスのみを対象にしていますが、両方のクラスを実装する必要があります。 小文字操作を実装するためのパターンとして、大文字操作を実装するための手順を使用します。  
  
1.  一連のプライベート フィールドを宣言します。  
  
     [!code-cs[VSSDKSmartTagTest#17](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_17.cs)]
     [!code-vb[VSSDKSmartTagTest#17](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_17.vb)]  
  
2.  フィールドを設定するコンストラクターを追加します。  
  
     [!code-cs[VSSDKSmartTagTest#18](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_18.cs)]
     [!code-vb[VSSDKSmartTagTest#18](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_18.vb)]  
  
3.  次のようにプロパティを設定します。  
  
     [!code-cs[VSSDKSmartTagTest#19](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_19.cs)]
     [!code-vb[VSSDKSmartTagTest#19](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_19.vb)]  
  
4.  範囲内のテキストを等価な大文字に置き換えることで、メソッド <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction.Invoke%2A> を実装します。  
  
     [!code-cs[VSSDKSmartTagTest#20](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_20.cs)]
     [!code-vb[VSSDKSmartTagTest#20](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_20.vb)]  
  
## コードのビルドとテスト  
 このコードをテストするには、SmartTagTest ソリューションをビルドし、実験用インスタンスで実行します。  
  
#### SmartTagTest ソリューションをビルドし、テストするには  
  
1.  ソリューションをビルドします。  
  
2.  デバッガーでこのプロジェクトを実行すると、Visual Studio の 2 つ目のインスタンスがインスタンス化されます。  
  
3.  テキスト ファイルを作成し、いくつかのテキストを入力します。  
  
     テキストの最初の単語の最初の文字の下に青い線が表示されます。  
  
4.  青い線の上にポインターを移動します。  
  
     ポインターの近くにボタンが表示されます。  
  
5.  ボタンをクリックすると、**Convert to upper case** と **Convert to lower case** という 2 つの提案されるアクションが表示されます。 最初の操作をクリックすると、現在の単語内のすべてのテキストが大文字に変換されます。 2 つ目の操作をクリックすると、すべてのテキストが小文字に変換されます。  
  
## 参照  
 [チュートリアル: ファイル名拡張子へのコンテンツの種類のリンク](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)