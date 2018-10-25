---
title: Blend における XAML のデバッグ |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 29a37182-2a2c-47e4-a4a9-2d5412738fed
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 50a4a65b0b8eadaeb065b71fcb7d31f6f0edd4db
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49815821"
---
# <a name="debug-xaml-in-blend"></a>Blend での XAML のデバッグ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

アプリの XAML をデバッグするために [!INCLUDE[blend_first](../includes/blend-first-md.md)] のツールを使用できます。 エラーが表示されます、プロジェクトをビルドすると、**結果**パネル。 エラーをダブルクリックして、エラーに関連するマークアップを検索します。 非表示にする場合は、作業領域を増やす必要があります、**結果**F12 キーを押してパネル。  
  
## <a name="syntax-errors"></a>構文エラー  
 構文エラーは、XAML または分離コード ファイルが言語のフォーマット規則に従っていない場合に発生します。 エラーの説明を参照すると、エラーの解決に役立ちます。 一覧では、エラーの発生しているファイルの名前と行番号も確認できます。 XAML エラーに一覧表示、**マークアップ** タブで、**結果**パネル。  
  
> [!TIP]
>  XAML は XML に基づくマークアップ言語で、XML 構文規則に従っています。  
  
 XAML 構文エラーのよくある原因は次のとおりです。  
  
- キーワードのスペルまたは大文字の表記に誤りがある。  
  
- 属性またはテキスト文字列の両側に引用符がない。  
  
- XAML 要素に終了タグがない。  
  
- XAML 要素が許可されていない場所にある。  
  
  共通 XAML 構文の詳細については、次を参照してください。[基本的な XAML 構文のガイド](http://go.microsoft.com/fwlink/?LinkId=329942)します。  
  
  また、[!INCLUDE[blend_subs](../includes/blend-subs-md.md)] での単純な分離コード構文エラー、コンパイル エラー、およびランタイム エラーを識別して、解決できます。 ただし、分離コード エラーは Visual Studio で識別して解決する方が簡単です。  
  
### <a name="debugging-sample-xaml-code"></a>サンプル XAML コードのデバッグ  
 次の例では、[!INCLUDE[blend_subs](../includes/blend-subs-md.md)] での単純な XAML デバッグ セッションを実行します。  
  
##### <a name="to-create-a-project"></a>プロジェクトを作成するには  
  
1. [!INCLUDE[blend_subs](../includes/blend-subs-md.md)]を開き、**ファイル**メニューをクリックして**新しいプロジェクト**です。  
  
    **新しいプロジェクト**ダイアログ ボックスで、左側にあるプロジェクトの種類の一覧が表示されます。 プロジェクトの種類をクリックすると、その種類に関連付けられているプロジェクト テンプレートが右側に表示されます。  
  
2. プロジェクトの種類の一覧でクリックして**XAML (Windows ストア)** します。  
  
3. プロジェクト テンプレートの一覧でクリックして**空のアプリ**します。  
  
4. **名前**テキスト ボックスに「`DebuggingSample`します。  
  
5. **場所**テキスト ボックスで、プロジェクトの場所を確認します。  
  
6. **言語**一覧で、 **Visual c#**、順にクリックします**OK**プロジェクトを作成します。  
  
7. デザイン サーフェイスを右クリックし、をクリックし、**ソースの表示**に切り替える**分割**ビュー。  
  
8. クリックして、次のコードをコピー、**コピー**コードの右上隅にあるリンクです。  
  
   ```  
   <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>  
        <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>  
   </Grid>  
  
   ```  
  
9. 既定値を見つける**グリッド**、開始タグと終了の間のコードを貼り付けると**グリッド**タグ。 完成したコードは次のようになります。  
  
    ```  
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">  
         <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>  
              <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>  
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">  
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>  
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>  
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>  
         </Grid>  
    </Grid>  
  
    ```  
  
10. Ctrl キーと Shift キーを押しながら B キーを押してプロジェクトをビルドします。  
  
    プロジェクトをビルドすることはできません、警告、エラー メッセージが表示されます、**結果**パネルが、エラーを一覧表示、アプリの下部に表示されます。  
  
    ![Blend for Visual Studio で XAML をデバッグ](../debugger/media/blend-debugxaml-xaml.png "blend_debugXAML_XAML")  
  
### <a name="resolving-xaml-errors"></a>XAML エラーの解決  
 XAML エラーが検出された場合、プロジェクトに無効なマークアップが含まれているという警告がデザイン サーフェスに表示されます。 エラーの一覧で、エラーを解決すると、**結果**パネルが更新されます。 すべてのエラーを解決すると、デザイン サーフェスが有効になり、アプリがデザイン サーフェスに表示されます。  
  
##### <a name="to-resolve-the-xaml-errors"></a>XAML エラーを解決するには  
  
1. リストの最初のエラーをダブルクリックします。 説明は、"値 '<' は、属性では無効です" となります。 エラーをダブルクリックすると、ポインターがコード内の対応する場所を見つけます。 `<` の前の `Button` は有効で、エラー メッセージで指定された属性ではありません。 コードの前の行を見ると、属性 `Top` の終わりの引用符がないことがわかります。 終わりの引用符を入力します。 エラーの一覧に注意してください、**結果** パネルが、変更を反映するように更新します。  
  
2. 説明をダブルクリックします"'0' が無効です、名前の先頭にある。"。 `Margin="0,149,0,0"` 正しい形式で表示されます。 ただし、`Margin` のカラー コーディングはコードの `Margin` の他のインスタンスと一致しないことに注意してください。 終わりの引用符が前の名前/値ペア (`VerticalAlignment="Top`) にないため、`Margin="` は前の属性の値の一部として読み込まれ、0 が名前/値ペアの先頭として読み込まれます。 `Top` の終わりの引用符を入力します。 [エラー一覧、**結果**] パネルが、変更を反映するように更新します。  
  
3. 残りのエラーをダブルクリックします。"終わりの XML タグ 'Button' が一致しません。" ポインターは、終了**グリッド**タグ (`</Grid>`)、内のエラーがあることを示します、`Grid`オブジェクト。 2 番目の `Button` オブジェクトで終わりのタグがないことに注意してください。 追加すると、終了`/`、**結果**パネルの一覧が更新されます。 これら 2 つの最初のエラーが解決され、さらに 2 つのエラーが識別されました。  
  
4. "メンバー 'content' が認識されないか、アクセスできません。" をダブルクリックします。 `c` の `content` は大文字になります。 小文字の "c" を大文字の "c" に置き換えます。  
  
5. ダブルクリック"プロパティに 'Mame' が存在しません、'<http://schemas.microsoft.com/winfx/2006/xaml>' 名前空間"。 "Mame" の "M" は "N" でなければなりません。 "M" を "N" で置き換えます。 これで、XAML が解析でき、アプリがデザイン サーフェスに表示されます。  
  
    ![Blend for Visual Studio で XAML をデバッグ](../debugger/media/blend-debugartboard-xaml.png "blend_debugArtboard_XAML")  
  
    Ctrl + Shift + B キーを押してプロジェクトをビルドし、残っているエラーがないことを確認します。  
  
## <a name="debugging-in-visual-studio"></a>Visual Studio でのデバッグ  
 アプリ内のコードをさらに簡単にデバッグするために、Visual Studio で [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] プロジェクトを開くことができます。 開くには、 [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] Visual Studio でプロジェクトでのプロジェクトを右クリックし、**プロジェクト**パネルをクリックして**Visual Studio で編集**。 Visual Studio でデバッグ セッションを完了したら、Ctrl + Shift + S キーを押してすべての変更を保存し、[!INCLUDE[blend_subs](../includes/blend-subs-md.md)] に戻ります。 プロジェクトの再読み込みを求めるメッセージが表示されます。 クリックして**すべてはい**操作を続行する[!INCLUDE[blend_subs](../includes/blend-subs-md.md)]します。  
  
 アプリのデバッグの詳細については、次を参照してください。 [Visual Studio でのデバッグの Windows ストア アプリ](http://go.microsoft.com/fwlink/?LinkId=329944)します。  
  
## <a name="getting-help"></a>ヘルプ情報の入手  
 デバッグのヘルプが必要な場合、[!INCLUDE[blend_subs](../includes/blend-subs-md.md)]アプリを検索できます、 [Windows ストア アプリのコミュニティ フォーラム](http://go.microsoft.com/fwlink/?LinkId=280308)投稿、問題に関連の質問を投稿します。



