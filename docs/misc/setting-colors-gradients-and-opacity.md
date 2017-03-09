---
title: "色、グラデーション、不透明度の設定 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "UI 要素のデザイン [Visual Studio SDK]"
ms.assetid: 1734bdc7-5e16-46c7-8507-eef5cea75cb9
caps.latest.revision: 31
caps.handback.revision: 31
manager: "douge"
---
# 色、グラデーション、不透明度の設定
Visual Studio におけるすべてのユーザー インターフェイス \(UI\) 要素は、Windows Presentation Foundation \(WPF\) で作成されます。 そのため、ツール ウィンドウやその他の UI 要素を作成するときにその要素に適切な属性を設定して、色、グラデーション、不透明度を適用できます。**\[プロパティ\]** ウィンドウを使用して特定の値を設定したり、システム値を調べるために統合開発環境 \(IDE\) に対するクエリを実行したりできます。 ご使用の拡張機能を IDE の他の部分と同じようにするには、システム値を使用することをお勧めします。  
  
 Windows フォーム UI とネイティブ コード UI は、下位互換性のために引き続きサポートされます。 WPF 以外の拡張機能で色とグラデーションを設定する方法については、[!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] ドキュメントをご覧ください。  
  
## 色、グラデーション、不透明度の設定  
 ほとんどの XAML 要素は `Background`、`Foreground`、`Opacity`、または他の視覚属性を設定すると外観を変更できます。 これらの属性は、<xref:System.Windows.Media.Brush?displayProperty=fullName> を値として取るプロパティに対応します  
  
#### ツール ウィンドウの背景色、グラデーション、不透明度を設定するには  
  
1.  MyControl.xaml を開きます。  
  
2.  **XAML** ウィンドウで、最上位レベルの <xref:System.Windows.Controls.UserControl> 要素に「`background=`」と入力します。  
  
     IntelliSense に、BackGround 属性に使用する色の一覧が表示されます。  
  
     一覧から色を選びます。  
  
3.  **\[プロパティ\]** ウィンドウで、**\[ブラシ\]** ノードを展開し、**\[バックグラウンド\]** をクリックします。  
  
     **\[プロパティ\]** ウィンドウには、カラー ピッカーが表示されます。 カラー ピッカーの上には、ブラシを表すアイコンの行があります。  
  
4.  スライダーを使用して、色を選択します。  
  
     XAML はすぐに更新を行い、新しい背景色が表示されます。  
  
5.  \[グラデーション ブラシ\] アイコンをクリックします。  
  
     カラー ピッカーが、グラデーション ピッカーに変わります。  
  
6.  スライダーを使用して、グラデーションを選択します。  
  
     XAML はすぐに更新を行い、新しいグラデーションが表示されます。  
  
7.  \[イメージ ブラシ\] アイコンをクリックします。  
  
     グラデーション ピッカーが、イメージ選択ツールに変わります。  
  
8.  イメージを選び、その伸縮パラメーターとタイル パラメーターを設定します。  
  
     XAML はすぐに更新を行い、新しい背景画像が表示されます。  
  
9. \[空のブラシ\] アイコンをクリックします。  
  
     デザイナーの背景がニュートラルに戻り、`BackGround` 属性が `"{x:Null}"` に設定されます。  
  
## システム値のクエリ実行  
 <xref:Microsoft.VisualStudio.Shell.VsBrushes?displayProperty=fullName> クラス プロパティを使用すると、システム値に対してクエリを実行できます。このプロパティは、Visual Studio の他の部分で設定されているブラシを参照します。  
  
#### システム値に対するクエリを実行して、色、グラデーション、不透明度を設定するには  
  
1.  XAML 要素を選びます。  
  
2.  要素の定義内で、要素の視覚属性の 1 つを `VsBrushes` クラスのプロパティに設定します。次の例を参考にしてください。  
  
     [!CODE [TWShortcutMenu#32](../CodeSnippet/VS_Snippets_VSSDK/twshortcutmenu#32)]  
  
     [DynamicResource](../Topic/DynamicResource%20Markup%20Extension.md) 拡張機能を使用すると、必要に応じて値を変更できます。たとえば、ユーザーが設定を変更する場合などです。`VsBrushes` クラスは既定の WPF 名前空間の一部ではないため、[X:static](../Topic/x:Static%20Markup%20Extension.md) 拡張機能を使用する必要があります。  
  
## 参照  
 [ツール ウィンドウの拡張](../misc/extending-tool-windows.md)