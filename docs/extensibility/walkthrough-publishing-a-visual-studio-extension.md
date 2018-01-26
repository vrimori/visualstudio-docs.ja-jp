---
title: "チュートリアル: Visual Studio 拡張機能の発行 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: be1402da1677388712472d4309c40ce767358f7b
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>チュートリアル: Visual Studio 拡張機能の発行

このチュートリアルでは、Visual Studio 拡張機能を Visual Studio Marketplace に発行する方法を示します。 開発者が使用して追加すると、拡張機能には、Marketplace、**拡張機能と更新**を新規および更新された拡張機能の参照があります。

## <a name="prerequisites"></a>必須コンポーネント

 このチュートリアルに従うには、Visual Studio SDK をインストールする必要があります。 詳細については、次を参照してください。 [、Visual Studio SDK をインストールする](../extensibility/installing-the-visual-studio-sdk.md)です。

## <a name="create-a-visual-studio-extension"></a>Visual Studio 拡張機能を作成します。

この場合、既定の VSPackage 拡張機能を使用しておが、同じ手順がすべての種類の拡張機能の有効です。

1. C# の場合、メニュー コマンドが使用できる"TestPublish"という名前の VSPackage を作成します。 詳細については、次を参照してください。 [、最初の拡張機能の作成: Hello World](../extensibility/extensibility-hello-world.md)です。

## <a name="package-your-extension"></a>拡張機能をパッケージ化

1. 製品名、作成者、およびバージョンに関する正しい情報で拡張 vsixmanifest を更新します。

  ![更新プログラムの拡張機能 vsixmanifest](media/update-extension-vsixmanifest.png)

2. 拡張機能を構築**リリース**モード。 今すぐ \bin\Release フォルダーに VSIX として、拡張機能をパッケージ化されます。

3. ダブルクリック、VSIX のインストール状態を確認します。

## <a name="test-the-extension"></a>拡張機能をテストします。

 拡張機能を配布する前に、ビルド、およびテストを Visual Studio の実験用インスタンスで、正しくインストールされていることを確認します。

1. Visual Studio でデバッグを開始します。 Visual Studio の実験用インスタンスを開きます。

2. 実験用インスタンスに移動、**ツール**メニューをクリックして**拡張機能と更新しています.**.TestPublish 拡張機能では、中央のペインでが表示され、有効にします。

3. **ツール** メニューの テスト コマンドを表示するかどうかを確認します。

## <a name="publish-the-extension-to-the-visual-studio-marketplace"></a>Visual Studio Marketplace 拡張機能を公開します。

1. 拡張機能のリリース バージョンが組み込まれていると、最新の状態であることを確認してください。

2. Web ブラウザーで開く、 [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) web サイトです。

3. 右上隅をクリックして**サインイン**です。

4. Microsoft アカウントを使用してサインインします。 Microsoft アカウントがない、この時点で作成することができます。

5. をクリックして**拡張機能を公開**です。  これを移動する、すべての拡張機能の管理ページにします。  発行元のアカウントを持っていない場合は、この時点で作成するのには促されます。

  ![Marketplace へのアップロードします。](media/upload-to-marketplace.png)

6. 使用して、拡張機能をアップロードするパブリッシャーを選択します。  発行元を変更するには、左側に表示されている発行元の名前をクリックするとします。  をクリックして**新しい拡張子**選択**Visual Studio**です。

7. **1: 拡張機能をアップロード**、Visual Studio Marketplace に直接 VSIX ファイルをアップロードまたはだけ、独自の web サイトへのリンクを追加することもできます。 この場合、拡張機能、TestPublish.vsix をアップロードします。  ドラッグして、拡張機能の削除を使用しても、  **をクリックして**ファイルを参照するリンクです。  拡張機能は、プロジェクトの \bin\Release フォルダーで確認できます。  **[続行]**をクリックします。

8. **2: 拡張機能の詳細を提供**、いくつかのフィールドは、自動設定された source.extension.vsixmanifest ファイル拡張機能からです。  それぞれの詳細については、下はあります。

    * **内部名**拡張機能の詳細ページの URL で使用されます。 例については、パブリッシャー名"myname"の下にある拡張機能を発行し、"myextension"である内部名を指定するがの URL"marketplace.visualstudio\.com/items?itemName=myname.myextension"の拡張機能の詳細ページ。
    
    * **表示名**の拡張機能です。  これは自動に設定された source.extension.vsixmanifest ファイルからです。
   
    * **バージョン**をアップロードする拡張機能の数。  これは自動に設定された source.extension.vsixmanifest ファイルからです。
    
    * **VSIX ID** Visual Studio は拡張機能を使用する一意の識別子を指定します。  自動更新する、拡張子が付いている場合に必要です。  これは自動に設定された source.extension.vsixmanifest ファイルからです。
    
   * **ロゴ**して拡張機能を使用します。  指定した場合は、source.extension.vsixmanifest ファイルの自動設定されたこのになります。
    
    * **短い説明文**は、拡張機能の内容。  Source.extension.vsixmanifest ファイルの自動設定されたこのになります。
    
    * **概要**スクリーン ショットと拡張機能の動作に関する詳細な情報を含めることをお勧めします。
    
    * **サポートされている Visual Studio バージョン**拡張機能は Visual Studio のバージョンで動作を選択することができます。  拡張機能は、これらのバージョンにのみインストールされます。
    
    * **サポートされている Visual Studio エディション**どのエディションの Visual Studio 拡張機能で動作を選択することができます。  拡張機能は、これらのエディションにのみインストールされます。
    
    * **[種類]**。  拡張機能の最も一般的な型は**ツール**です。
    
    * **カテゴリ**です。  最大 3 つの拡張機能に最適なであるを選択します。
    
    * **タグ**キーワードによってユーザーは、拡張機能を検索します。 タグは、Marketplace で、拡張機能の検索の適合性を向上できます。
    
    * **カテゴリの料金**拡張機能のコストします。
    
    * **ソース コード リポジトリ**コミュニティで、ソース コードへのリンクを共有することができます。
    
    * **拡張機能の Q & A を許可する**によりユーザーは、拡張機能エントリ ページ上の質問のままにします。

9. をクリックして**保存およびアップロード**です。 これは、操作により、パブリッシャーへの管理 ページ。  拡張機能はまだ公開されていません。  拡張機能と選択 を右クリックし、拡張機能を公開する**公開**です。  どの拡張機能のようになります Marketplace でを選択して表示できます**表示拡張機能**します。  買収番号 をクリックして**レポート**です。  をクリックして拡張機能を変更するには、**編集*です。

  ![拡張機能エントリ メニュー](media/extension-entry-menu.png)

10. クリックした後**公開**、拡張機能がパブリックようになりました。  拡張機能の Visual Studio Marketplace を検索します。

## <a name="add-additional-users-to-manage-your-publisher-account"></a>発行元のアカウントを管理するユーザーを追加します。

Marketplace は、アクセスし、発行元のアカウントを管理するその他のユーザー権限の許可をサポートします。

1. ユーザーを追加するパブリッシャーのアカウントに移動します。

2. 選択**メンバー**  をクリック**追加**

  ![追加のユーザーを追加します。](media/add-users.png)

3. 追加し、適切なレベルの下にあるアクセスを付与するユーザーの電子メール アドレスを指定できます**ロールを選択して**です。  次のオプションから選択できます。

  * **作成者**: ユーザーの拡張機能を公開ができない表示または管理できる他のユーザーによって公開された拡張機能です。
  
  * **リーダー**: ユーザーから、拡張機能の表示しますが、パブリッシュことはできません、または拡張機能を管理します。
  
  * **共同作成者**: ユーザーをパブリッシュし、拡張機能を管理ことはできませんパブリッシャーの設定を編集またはアクセスを管理します。
  
  * **所有者**: ユーザーが発行し拡張機能を管理、パブリッシャーの設定を編集してのアクセスを管理します。
  
## <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Visual Studio Marketplace から、拡張機能をインストールします。

これで、拡張機能を発行すると、Visual Studio にインストールし、テストします。

1. Visual Studio での**ツール** メニューのをクリックして**拡張機能と更新しています.**.

2. をクリックして**オンライン**TestPublish を検索します。

3. **[ダウンロード]**をクリックします。 拡張機能は、インストールのスケジュールされます。

4. インストールを完了するには、Visual Studio のすべてのインスタンスを閉じます。

## <a name="remove-the-extension"></a>拡張機能を削除します。

お使いのコンピューターと Visual Studio Marketplace から、拡張機能を削除できます。

### <a name="to-remove-the-extension-from-the-visual-studio-marketplace"></a>Visual Studio Marketplace から、拡張機能を削除するには

1. 開く、 [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) web サイトです。

2. 右上隅にあるをクリックして**発行**拡張機能です。  TestPublish を発行するために使用するパブリッシャーを選択します。  TestPublish の一覧が表示されます。

3. 拡張機能エントリを右クリックし、をクリックして**削除**拡張機能を削除することを確認するように求められます。  **[OK]**をクリックします。

### <a name="to-remove-the-extension-from-your-computer"></a>お使いのコンピューターから、拡張機能を削除するには

1. Visual Studio での**ツール** メニューのをクリックして**拡張機能と更新しています.**.

2. TestPublish を選択し、クリックして**アンインストール**です。 拡張機能は、アンインストールがスケジュールされます。

3. アンインストールを完了するには、Visual Studio のすべてのインスタンスを閉じます。
