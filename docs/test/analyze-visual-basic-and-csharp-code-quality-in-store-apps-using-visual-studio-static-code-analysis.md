---
title: "Visual Studio 静的コード分析によるストア アプリの Visual Basic および C# のコード品質の分析 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.propertypages.csvb.express"
ms.assetid: cab553fc-19a9-4cbf-858e-8200258ffe50
caps.latest.revision: 14
caps.handback.revision: 14
author: "erickson-doug"
ms.author: "douge"
manager: "douge"
---
# Visual Studio 静的コード分析によるストア アプリの Visual Basic および C# のコード品質の分析
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![Windows と Windows Phone に適用されます](~/docs/debugger/media/windows_and_phone_content.png "windows\_and\_phone\_content")  
  
 Visual Studio Express のコード分析ツールは、コードを調べてプログラミング上の一般的な問題や違反がないことを確認します。  コード分析の警告はコンパイラのエラーや警告とは異なります。コード分析ツールは、有効であってもコードの作成者やコードを利用する他のユーザーにとって問題になる可能性がある特定のコード パターンを検索します。  また、コード分析では、テストでは検出できないコードの欠陥を見つけることができます。  開発プロセス中に定期的にコード分析ツールを実行することで、高品質なアプリを完成させることができます。  
  
> [!NOTE]
>  Visual Studio Ultimate、Visual Studio Premium、および Visual Studio Professional では、コード分析の全機能を使用できます。  MSDN ライブラリの「[コード分析ツールを使用したアプリケーション品質の分析](http://msdn.microsoft.com/library/dd264897.aspx)」を参照してください。  
  
## このトピックの内容  
 以下について説明します。  
  
 [コード分析の実行](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Run)  
  
 [コード分析警告の分析と解決](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Analyze)  
  
 [コード分析警告の抑制](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Suppress)  
  
 [コード分析結果の検索とフィルター処理](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Search)  
  
 [Visual Basic および C# コード分析警告](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Warnings)  
  
##  <a name="BKMK_Run"></a> コード分析の実行  
 Visual Studio ソリューションでコード分析を実行するには:  
  
-   **\[ビルド\]** メニューの **\[ソリューションでコード分析を実行\]** をクリックします。  
  
 プロジェクトをビルドするたびに自動的にコード分析を実行するには:  
  
1.  ソリューション エクスプローラーでプロジェクト名を右クリックし、**\[プロパティ\]** をクリックします。  
  
2.  プロジェクトのプロパティ ページで、**\[コード分析\]** をクリックして、**\[ビルドに対するコード分析の有効化 \(定数 CODEANALYSIS を定義\)\]** をクリックします。  
  
 ソリューションがコンパイルされ、コード分析が実行されます。  結果は、\[コード分析\] ウィンドウに表示されます。  
  
 ![&#91;コード分析&#93; ウィンドウ](../test/media/ca_managed_collapsed.png "CA\_Managed\_Collapsed")  
  
##  <a name="BKMK_Analyze"></a> コード分析警告の分析と解決  
 特定の警告を分析するには、\[コード分析\] ウィンドウで警告のタイトルをクリックします。  警告が展開され、問題に関する詳細情報が表示されます。  
  
 ![展開されたコード分析の警告](../test/media/ca_managed_callouts.png "CA\_Managed\_Callouts")  
  
 警告を展開すると、警告の原因となったコード行が Visual Studio のコード エディターで強調表示されます。  
  
 ![コード分析テキストの強調表示](~/docs/test/media/ca_managed_sourceline.png "CA\_Managed\_SourceLine")  
  
 何が問題かを理解したら、コードを修正してそれを解決できます。  コード分析を再度実行して、\[コード分析\] ウィンドウに警告が表示されないこと、および修正によって新しい警告が発生しないことを確認します。  
  
> [!TIP]
>  コード分析は、\[コード分析\] ウィンドウから再実行できます。  **\[分析\]** をクリックし、分析の範囲を選択します。  ソリューション全体または選択したプロジェクトの分析を再実行できます。  
  
##  <a name="BKMK_Suppress"></a> コード分析警告の抑制  
 コード分析警告の修正を行わないことを決定する場合があります。  コードを実装したときの警告の発生確率と、警告を解決するためのコード変更の量を比較して、解決しないことを選択できます。  または、警告で使用された分析が特定のコンテキストでは不適切であると判断できます。  個々の警告を抑制して、\[コード分析\] ウィンドウに表示されないように設定できます。  
  
 警告を抑制するには:  
  
1.  詳細情報が表示されていない場合は、警告のタイトルをクリックして展開します。  
  
2.  警告の下部にある **\[アクション\]** リンクをクリックします。  
  
3.  **\[メッセージの非表示\]** をポイントし、**\[ソース内\]** または **\[抑制ファイル内\]** をクリックします。  
  
    -   **\[ソース内\]** をクリックすると、警告を生成したメソッドの上のソース ファイルに `SuppressMessage` 属性が挿入されます。  これにより、抑制が検出されやすくなります。  
  
    -   **\[抑制ファイル内\]** では、プロジェクトの `SuppressMessage` ファイルに **GlobalSuppressions.cs** 属性を追加します。  これにより、抑制を簡単に管理できるようになります。  `SuppressMessage` に追加された **GlobalSuppression.cs** 属性は、警告を生成したメソッドもターゲットとすることに注意してください。  警告がグローバルに表示なしになることはありません。  
  
     ソース ファイルで警告を抑制するか、抑制ファイルで警告を抑制するかは、コーディング スタイルとニーズによって決まります。  
  
##  <a name="BKMK_Search"></a> コード分析結果の検索とフィルター処理  
 警告メッセージの長い一覧の検索と、複数のプロジェクトから成るソリューションの警告をフィルター処理できます。  
  
 ![&#91;コード分析&#93; ウィンドウの検索とフィルター処理](../test/media/ca_searchfilter.png "CA\_SearchFilter")  
  
 [!INCLUDE[vs_dev11_expwin_long](../misc/includes/vs_dev11_expwin_long_md.md)] では、コード分析のすべての警告に、警告の重大度レベルが示されています。  
  
##  <a name="BKMK_Warnings"></a> Visual Basic および C\# コード分析警告  
 コード分析では次の警告が発生します。  
  
 [CA1001: 破棄可能なフィールドを所有する型は、破棄可能でなければなりません](http://msdn.microsoft.com/library/ms182172.aspx)  
  
 [CA1821: 空のファイナライザーを削除します](http://msdn.microsoft.com/en-us/library/bb264476.aspx)  
  
 [CA2213: 破棄可能なフィールドは破棄されなければなりません](http://msdn.microsoft.com/en-us/library/ms182328.aspx)  
  
 [CA2229: シリアル化コンストラクターを実装します](http://msdn.microsoft.com/en-us/library/ms182343.aspx)  
  
 [CA2231: ValueType.Equals のオーバーライドで、演算子 equals をオーバーロードします](http://msdn.microsoft.com/en-us/library/ms182359.aspx)