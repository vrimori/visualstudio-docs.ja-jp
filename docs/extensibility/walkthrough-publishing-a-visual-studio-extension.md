---
title: 'チュートリアル: Visual Studio 拡張機能の発行 |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0bb77683187bcb50c1aa5a4f599610acdbf1ac45
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55038345"
---
# <a name="walkthrough-publish-a-visual-studio-extension"></a>チュートリアル: Visual Studio 拡張機能を公開します。

このチュートリアルでは、Visual Studio 拡張機能を Visual Studio Marketplace に発行する方法を示します。 開発者が使用できる、拡張機能を Marketplace に追加すると**拡張機能と更新**新規および更新された拡張機能を参照します。

## <a name="prerequisites"></a>必須コンポーネント

 このチュートリアルに従うには、Visual Studio SDK をインストールする必要があります。 詳細については、"[Visual Studio SDK をインストール](../extensibility/installing-the-visual-studio-sdk.md)"を参照してください。

## <a name="create-a-visual-studio-extension"></a>Visual Studio 拡張機能を作成します。

この記事では、既定の VSPackage 拡張機能を使用してが、手順は拡張機能のすべての種類に対して無効です。

1. C# という名前の VSPackage を作成`TestPublish`を持つメニュー コマンド。 詳細については、次を参照してください。[初めての拡張機能を作成します。Hello World](../extensibility/extensibility-hello-world.md)します。

## <a name="package-your-extension"></a>拡張機能をパッケージ化します。

1. 拡張機能の更新 *.vsixmanifest*製品名、作成者、およびバージョンの詳細については、正しい情報。

   ![更新プログラムの拡張機能の vsixmanifest](media/update-extension-vsixmanifest.png)

2. 拡張機能を構築**リリース**モード。 拡張機能が \bin\Release フォルダーで、VSIX としてパッケージ化されます。

3. インストールを確認する VSIX をダブルクリックすることができます。

## <a name="test-the-extension"></a>拡張機能をテストします。

 拡張機能を配布する前にビルドしてテストを Visual Studio の実験用インスタンスで正しくインストールされていることを確認します。

1. Visual Studio では、Visual Studio の実験用インスタンスを開くデバッグを開始します。

2. 実験用のインスタンスに移動、**ツール**メニューをクリックします**拡張機能と更新**します。 TestPublish 拡張機能では、中央のウィンドウに表示する必要があり、有効にします。

3. **ツール** メニューの テスト コマンドを表示するかどうかを確認します。

## <a name="publish-the-extension-to-the-visual-studio-marketplace"></a>拡張機能を Visual Studio Marketplace に公開します。

1. 拡張機能のリリース バージョンが組み込まれているし、最新の状態であるようにします。

2. Web ブラウザーで開く、 [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) web サイト。

3. 右上隅にある次のようにクリックします。**サインイン**します。

4. Microsoft アカウントを使用してサインインします。 Microsoft アカウントがない、この時点で作成できます。

5. クリックして**拡張機能を公開**します。  このオプションでは、すべての拡張機能の管理ページに移動します。 発行元アカウントを持っていない場合は、この時点で 1 つを作成する求められます。

   ![Marketplace へのアップロードします。](media/upload-to-marketplace.png)

6. 拡張機能のアップロードに使用するパブリッシャーを選択します。 発行元を変更するには、左側に表示されている発行元の名前をクリックします。 をクリックして**新しい拡張機能**選択**Visual Studio**します。

7. **1。拡張機能のアップロード**、Visual Studio Marketplace に直接 VSIX ファイルをアップロードするか、独自の web サイトにリンクを追加することもできます。 この例では、拡張機能で*TestPublish.vsix*アップロードされます。 ドラッグ アンド、拡張機能を削除するかを使用して、**クリックして**ファイルを参照するリンク。 プロジェクトの \bin\Release フォルダーで、拡張機能を検索します。  **[続行]** をクリックします。

8. **2。拡張機能の詳細を提供**、一部のフィールドが自動設定から、 *source.extension.vsixmanifest*拡張機能からのファイル。 以下のそれぞれについて詳細を検索するには。

    * **内部名**拡張機能の詳細ページの URL で使用されます。 例については、発行元名"myname"拡張機能を公開して、「my の拡張」となるように内部の名前を指定する結果の URL"marketplace.visualstudio\.com/items?itemName=myname.myextension"拡張機能の詳細ページです。
    
    * **表示名**の拡張機能。 この名前はから自動的に設定されます、 *source.extension.vsixmanifest*ファイル。
   
    * **バージョン**をアップロードする拡張機能の数。 このバージョンはから自動的に設定されます、 *source.extension.vsixmanifest*ファイル。
    
    * **VSIX ID**拡張機能の Visual Studio を使用する一意の識別子です。 自動的に更新され、拡張機能がある場合、この識別子が必要です。 この識別子は、自動設定から、 *source.extension.vsixmanifest*ファイル。
    
   * **ロゴ**拡張機能に使用されます。 このロゴはから自動的に設定されます、 *source.extension.vsixmanifest*ファイル指定されている場合。
    
     * **短い説明文**は、拡張機能の内容。 この説明はから自動的に設定されます、 *source.extension.vsixmanifest*ファイル。
    
     * **概要**スクリーン ショットと、拡張機能の動作に関する詳細な情報を含めることをお勧めします。
    
     * **サポートされている Visual Studio バージョン**拡張機能は Visual Studio のバージョンで動作を選択できます。 拡張機能は、これらのバージョンにのみインストールされます。
    
     * * * Visual Studio のエディションでは、拡張機能が取り組む Visual Studio のエディションを選択できます。 サポートされています。 拡張機能は、これらのエディションにのみインストールされます。
    
     * **[種類]**。 拡張機能の最も一般的な型は**ツール**します。
    
     * **カテゴリ**します。 拡張機能に最適なは最大 3 の種類を選択します。
    
     * **タグ**キーワードによってユーザーは、拡張機能を検索します。 タグは、Marketplace で、拡張機能の検索の関連性を向上させることができます。
    
     * **価格カテゴリ**拡張機能のコストです。
    
     * **ソース コード リポジトリ**コミュニティで、ソース コードへのリンクを共有することができます。
    
     * **拡張機能の Q & A を許可する**拡張機能のエントリ ページに質問を残すことができます。

9. クリックして**を保存してアップロード**します。 このオプションにより、パブリッシャーには、ページを管理します。 拡張機能はまだ公開されていません。 拡張機能を公開するには、拡張機能を選択しますを右クリックして**公開**します。 どの拡張機能のようになります Marketplace でを選択して表示できます**拡張機能の表示**します。 購入の数字、 をクリックして**レポート**します。 拡張機能を変更するには、をクリックして**編集**します。

   ![エントリの拡張機能メニュー](media/extension-entry-menu.png)

10. クリックすると**公開**、拡張機能がパブリックになりました。 拡張機能の Visual Studio Marketplace を検索します。

## <a name="add-additional-users-to-manage-your-publisher-account"></a>発行元アカウントを管理するユーザーを追加します。

Marketplace では、アクセスし、発行元アカウントを管理するその他のユーザー権限の付与をサポートします。

1. ユーザーを追加するパブリッシャーのアカウントに移動します。

2. 選択**メンバー**  をクリック**追加**します。

   ![追加のユーザーを追加します。](media/add-users.png)

3. 追加し、適切なレベルのアクセスを付与するユーザーの電子メール アドレスを指定することができますし、**ロールを選択**します。  次のオプションから選択できます。

   * **作成者**:ユーザー拡張機能の発行ことはできません表示したり他のユーザーによって発行された拡張機能を管理できます。
  
   * **リーダー**:ユーザー表示拡張機能ことはできません発行したり拡張機能を管理できます。
  
   * **共同作成者**:ユーザー発行し、拡張機能の管理ことはできませんパブリッシャーの設定を編集したりアクセスを管理できます。
  
   * **所有者**:ユーザーは、発行、拡張機能を管理し、パブリッシャーの設定を編集、およびアクセスを管理できます。
  
## <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Visual Studio Marketplace から拡張機能をインストールします。

これで、拡張機能を公開すると、Visual Studio にインストールし、テストします。

1. Visual Studio での**ツール** メニューのをクリックして**拡張機能と更新**します。

2. クリックして**オンライン**し検索**TestPublish**します。

3. **[ダウンロード]** をクリックします。 拡張機能は、インストールのスケジュール設定します。

4. インストールを完了するには、Visual Studio のすべてのインスタンスを閉じます。

## <a name="remove-the-extension"></a>拡張機能を削除します。

お使いのコンピューターと、Visual Studio Marketplace から拡張機能を削除できます。

### <a name="to-remove-the-extension-from-the-visual-studio-marketplace"></a>Visual Studio Marketplace から拡張機能を削除するには

1. 開く、 [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) web サイト。

2. 右上隅にある次のようにクリックします。**発行**拡張機能。 発行するために使用するパブリッシャーを選択**TestPublish**します。 一覧で**TestPublish**が表示されます。

3. 拡張機能のエントリを右クリックし、をクリックして**削除**します。 拡張機能を削除するかどうかの確認を求められます。 **[OK]** をクリックします。

### <a name="to-remove-the-extension-from-your-computer"></a>お使いのコンピューターから、拡張機能を削除するには

1. Visual Studio での**ツール** メニューのをクリックして**拡張機能と更新**します。

2. 選択**TestPublish**し**アンインストール**します。 拡張機能からアンインストールされる予定です。

3. アンインストールを完了するには、Visual Studio のすべてのインスタンスを閉じます。
