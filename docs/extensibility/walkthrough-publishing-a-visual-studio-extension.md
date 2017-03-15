---
title: "チュートリアル: Visual Studio 拡張機能を公開する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
caps.latest.revision: 17
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
ms.sourcegitcommit: 574af4ff2b3858201c13121475de02a763572f6b
ms.openlocfilehash: fcfb0724b89d60553d6686a0705ab1e9459014ce
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>チュートリアル: Visual Studio 拡張機能を公開します。
このチュートリアルでは、Visual Studio 拡張機能を Visual Studio ギャラリーに発行する方法を示します。 開発者が使用して、ギャラリーに、拡張機能を追加するときに**拡張機能と更新プログラム**新規および更新された拡張機能を参照します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルに従うには、Visual Studio SDK をインストールする必要があります。 詳細については、次を参照してください。 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)します。  
  
## <a name="create-a-visual-studio-extension"></a>Visual Studio 拡張機能を作成します。  
 ここで、既定の VSPackage 拡張機能を使用してされますが、同じ手順は、すべての拡張機能について。  
  
1.  C# という名前の VSPackage を作成する`TestPublishing`を持つメニュー コマンドです。 詳細については、次を参照してください。[メニュー コマンドを使用して拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)します。  
  
## <a name="test-the-extension"></a>拡張機能をテストします。  
 拡張機能を配布する前にビルドしてテストを行い、Visual Studio の実験用インスタンスで、正しくインストールされていることを確認します。  
  
1.  Visual Studio でデバッグを開始します。 Visual Studio の実験用インスタンスを開きます。  
  
2.  実験用インスタンスで、**ツール**メニューをクリック**拡張機能マネージャー**します。 TestPublishing 拡張機能では、中央のウィンドウが表示されを有効にします。  
  
3.  **ツール** メニューの テスト コマンドを表示するかどうかを確認します。  
  
## <a name="publish-the-extension-to-the-visual-studio-gallery"></a>拡張機能を Visual Studio ギャラリーに公開します。  
 ここで、拡張機能を Visual Studio ギャラリーに発行できます。  
  
1.  拡張機能のリリース バージョンが組み込まれているが最新であることを確認してください。  
  
2.  Web ブラウザーで、 [Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkId=194329) の Web サイトを開きます。  
  
3.  右下隅で  **SIGN IN**します。  
  
4.  Microsoft アカウントを使用してサインインします。 Microsoft アカウントがない、この時点で作成することができます。  
  
5.  **[アップロード]**をクリックします。  
  
6.  **手順 1: 拡張機能の種類****ツール**順にクリック**次**します。  
  
7.  **手順 2: アップロード**、Visual Studio ギャラリーに直接アップロードまたはだけ独自の web サイトへのリンクを追加することもできます。 ここで **ツールをアップロードしたいと考えて**します。 **Control の選択**ボックスが表示されます。 クリックして**参照**し、プロジェクトの \bin\Release フォルダーで TestPublish.vsix を選択します。 **[次へ]**をクリックします。  
  
8.  **手順 3: 基本情報**、source.extension.vsixmanifest ファイルのフィールドが表示されます。 適切な選択**カテゴリ**追加**タグ**拡張機能を見つけられるようにします。 詳細な概要と説明 (説明は少なくとも 280 文字で指定する必要があります) を追加することがあります。 ままにして**拡張機能の種類**として**Microsoft 拡張機能ではない**と**原価カテゴリ**として**試用**します。  
  
9. ページの下部にある投稿物に関する契約を読み、確認**同意**します。  
  
10. クリックして**投稿を作成する**です。 これには、拡張機能がオンで、ページがまだ発行されているメッセージに、Visual Studio ギャラリー ページが表示されます。  
  
11. **[発行]**をクリックします。  
  
12. 拡張機能の Visual Studio ギャラリーを検索します。 TestPublish 拡張機能の一覧が表示されます。  
  
## <a name="install-the-extension-from-the-visual-studio-gallery"></a>Visual Studio ギャラリーから拡張機能をインストールします。  
 拡張機能を発行すると、Visual Studio にインストールし、存在テストします。  
  
1.  Visual Studio での**ツール** メニューのをクリックして**拡張機能と更新プログラム**します。  
  
2.  クリックして**オンライン**TestPublish を検索します。 TestPublish 拡張機能の一覧が表示されます。  
  
3.  **[ダウンロード]**をクリックします。 拡張機能をダウンロードした後、 **[インストール]**をクリックします。  
  
4.  インストールが完了するには、Visual Studio を再起動します。  
  
## <a name="removing-the-extension"></a>拡張機能の削除  
 Visual Studio ギャラリーおよびお使いのコンピューターから、拡張機能を削除できます。  
  
#### <a name="to-remove-the-extension-from-the-visual-studio-gallery"></a>Visual Studio ギャラリーから、拡張機能を削除するには  
  
1.  開いている、 [Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkId=194329) web サイトです。  
  
2.  [中央] をクリックして**My 拡張**します。 TestPublish の一覧が表示されます。  
  
3.  クリックして**削除**します。  
  
#### <a name="to-remove-the-extension-from-your-computer"></a>お使いのコンピューターから、拡張機能を削除するには  
  
1.  Visual Studio の **[ツール]** メニューで、 **[拡張機能マネージャー]**をクリックします。  
  
2.  TestPublish を選択し、クリックして**アンインストール**します。  
  
3.  アンインストールを完了するには、Visual Studio を再起動します。

