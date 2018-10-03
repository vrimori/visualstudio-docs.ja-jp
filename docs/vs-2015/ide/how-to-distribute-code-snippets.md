---
title: '方法: コード スニペットを配布する | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code snippets, distributing
ms.assetid: 5f717abd-e167-47ae-818c-6b0bae100ceb
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2bda2aa5e7639b951b0df6bb83ff2d50fd4331e7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47535850"
---
# <a name="how-to-distribute-code-snippets"></a>方法: コード スニペットを配布する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: コード スニペットを配布](https://docs.microsoft.com/visualstudio/ide/how-to-distribute-code-snippets)します。  
  
コード スニペットは、友人に配布することができます。友人は、コード スニペット マネージャーを使用して、そのスニペットを自分のコンピューターにインストールできます。 ただし、配布するスニペットが複数ある場合や、スニペットをより広範に配布する場合は、スニペット ファイルを Visual Studio 拡張機能に含めると、Visual Studio ユーザーはこれをインストールできます。  
  
 Visual Studio 拡張機能を作成するには、Visual Studio SDK をインストールする必要があります。 Visual Studio のインストールと一致する VSSDK のバージョンを見つける[Visual Studio 2015 のダウンロード](http://www.visualstudio.com/downloads/visual-studio-2015-downloads-vs.aspx)します。  
  
## <a name="setting-up-the-extension"></a>拡張機能を設定する  
 この手順では、「[チュートリアル: コード スニペットを作成する](../ide/walkthrough-creating-a-code-snippet.md)」で作成したのと同じ Hello World コード スニペットを使います。 .snippet のテキストは用意されているため、前の手順に戻ってコード スニペットを作成する必要はありません。  
  
1.  **TestSnippet** という新しい VSIX プロジェクトを作成します  (**[ファイル] > [新規作成] > [プロジェクト] > [Visual C#]\(または [Visual Basic]) > [拡張]**)。  
  
2.  **TestSnippet** プロジェクトで新しい XML ファイルを追加し、**VBCodeSnippet.snippet** という名前を付けます。 内容を次のコードに置き換えます。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <CodeSnippets  
        xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
      <CodeSnippet Format="1.0.0">  
        <Header>  
          <Title>Hello World VB</Title>  
          <Shortcut>HelloWorld</Shortcut>  
          <Description>Inserts code</Description>  
          <Author>MSIT</Author>  
          <SnippetTypes>  
            <SnippetType>Expansion</SnippetType>  
            <SnippetType>SurroundsWith</SnippetType>  
          </SnippetTypes>  
        </Header>  
        <Snippet>  
          <Code Language="VB">  
            <![CDATA[Console.WriteLine("Hello, World!")]]>  
          </Code>  
        </Snippet>  
      </CodeSnippet>  
    </CodeSnippets>  
    ```  
  
#### <a name="setting-up-the-directory-structure"></a>ディレクトリ構造の設定  
  
1.  ソリューション エクスプ ローラーでプロジェクト ノードを選択し、フォルダーを追加します。その名前は、コード スニペット マネージャーでスニペットに付けるのと同じ名前にします。 ここでは、**HelloWorldVB** になります。  
  
2.  .snippet ファイルを **HelloWorldVB** フォルダーに移動します。  
  
3.  ソリューション エクスプローラーで .snippet ファイルを選び、**[プロパティ]** ウィンドウで **[ビルド アクション]** を **[コンテンツ]** に、**[出力ディレクトリにコピー]** を **[常にコピーする]** に、**[VSIX に含める]** を **[true]** に、それぞれ設定します。  
  
#### <a name="adding-the-pkgdef-file"></a>.pkgdef ファイルの追加  
  
1.  **HelloWorldVB** フォルダーにテキスト ファイルを追加し、**HelloWorldVB.pkgdef** という名前を付けます。 このファイルは、レジストリにキーを追加するために使用します。 ここでは、新しいキーを  
  
     **HKCU\Software\Microsoft\VisualStudio\14.0\Languages\CodeExpansions\Basic** に追加します。  
  
2.  ファイルに次の行を追加します。  
  
    ```  
    // Visual Basic   
    [$RootKey$\Languages\CodeExpansions\Basic\Paths]   
    "HelloWorldVB"="$PackageFolder$"  
    ```  
  
     このキーを調べると、さまざまな言語を指定する方法が分かります。  
  
3.  ソリューション エクスプローラーで .pkgdef ファイルを選び、**[プロパティ]** ウィンドウで **[ビルド アクション]** を **[コンテンツ]** に、**[出力ディレクトリにコピー]** を **[常にコピーする]** に、**[VSIX に含める]** を **[true]** に、それぞれ設定します。  
  
4.  VSIX マニフェストに .pkgdef ファイルを資産として追加します。 source.extension.vsixmanifest ファイルで、**[資産]** タブに移動し、**[新規]** をクリックします。  
  
5.  **[新しい資産の追加]** ダイアログ ボックスで、**[型]** を **Microsoft.VisualStudio.VsPackage** に、**[種類]** を **[ファイル システム上のファイル]** に、**[パス]** を **[HelloWorldVB.pkgdef]** (ドロップダウン リストに表示される) に、それぞれ設定します。  
  
### <a name="testing-the-snippet"></a>スニペットのテスト  
  
1.  これで、コード スニペットが Visual Studio の実験用インスタンスで動作することを確認できるようになりました。 実験用インスタンスとは、コードの記述に使用する Visual Studio とは異なる、Visual Studio のもう 1 つのコピーです。 これを使用することにより、開発環境に影響を与えずに、拡張機能を処理することができます。  
  
2.  プロジェクトをビルドし、デバッグを開始します。 Visual Studio の 2 番目のインスタンスが表示されます。  
  
3.  実験用インスタンスで、**[ツール] > [コード スニペット マネージャー]** に移動し、**[言語]** を **[基本]** に設定します。 フォルダーの 1 つとして HelloWorldVB が表示されるはずです。そのフォルダーを展開すると HelloWorldVB スニペットを表示できます。  
  
4.  スニペットをテストします。 実験用インスタンスで、Visual Basic プロジェクトを開き、コード ファイルのいずれかを開きます。 コードの任意の場所にカーソルを置いて右クリックし、コンテキスト メニューで **[スニペットの挿入]** を選びます。  
  
5.  フォルダーの 1 つとして HelloWorldVB が表示されるはずです。 これをダブルクリックします。 **[スニペットの挿入: HellowWorldVB >]** ポップアップが表示されます。ここに **[HelloWorldVB]** ドロップダウン リストが表示されます。 [HelloWorldVB] ドロップダウン リストをクリックします。 次の行がファイルに追加されます。  
  
    ```vb  
    Console.WriteLine("Hello, World!")  
    ```  
  
## <a name="see-also"></a>関連項目  
 [コード スニペット](../ide/code-snippets.md)


