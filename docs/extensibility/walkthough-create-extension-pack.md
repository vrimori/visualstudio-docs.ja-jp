---
title: 拡張機能パック項目テンプレートを使用して、拡張機能パックを作成する |Microsoft Docs
ms.custom: ''
ms.date: 07/27/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: chitray
ms.author: chitray
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: 2e0215b22c66d6b555650e05985a674f2ad9aed4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49943103"
---
# <a name="walkthrough-create-an-extension-pack"></a>チュートリアル: 拡張機能パックを作成する

拡張機能パックには、一連の拡張機能を一緒にインストールすることができます。 拡張機能パックを使用すると、簡単にお気に入りの拡張機能を他のユーザーに共有または特定のシナリオの拡張機能のセットをバンドルできます。
  
## <a name="prerequisites"></a>必須コンポーネント

Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  

拡張機能パックの機能は、Visual Studio 15.8 Preview 2 以降から使用できます。
  
## <a name="create-an-extension-with-an-extension-pack-item-template"></a>拡張機能を拡張パック項目テンプレートの作成します。

拡張機能パック項目テンプレートは、一緒にインストールすることができる拡張機能のセットを拡張機能パックを作成します。
  
1. **新しいプロジェクト** ダイアログ ボックスで、展開**Visual c#** または**Visual Basic**順にクリックします**Extensibility**します。 **テンプレート**ペインで、 **VSIX プロジェクト**します。 **[名前]** ボックスに「 `Test Extension Pack`」と入力します。 **[OK]** をクリックします。  
  
2. **ソリューション エクスプ ローラー**でプロジェクト ノードを右クリックし、選択**追加/新しい項目の**します。 移動する、Visual c#**拡張**ノード**拡張パック**します。 既定のファイル名 (ExtensionPack1.cs) のままにします。  
  
3. 次のコードを含む、ExtensionPack1.vsext ファイルが追加されます。

   ```json
   {
    "id": "ExtensionPack1",
    "name": "ExtensionPack1",
    "description": "Read about creating extension packs at https://aka.ms/vsextpack",
    "version": "1.0.0.0",
    "extensions": [  // List of extensions that are included in the Extension Pack.
      {
        "vsixId": "41858b2d-ff0b-4a43-80b0-f1b2d6084935", // The vsix id of the extension you want to   include.
        "name": "AlignAssignments"
      },
      {
          "vsixId": "42374550-426a-400e-96f9-237682e8dea6",
        "name": "CopyAsHtml"
      }
    ]
   }  
   ```

4. 拡張機能パックに含めない拡張機能の vsixid で確認できます、 [Visual Studio Marketplace](https://marketplace.visualstudio.com/)します。 拡張機能を含める をクリックする**コピー ID**します。 既存を更新する**vsixId**上記のファイルまたはリストに別の拡張機能を追加します。

    ![Marketplace から VsixId をコピーします。](media/vsixid-marketplace.png)

5. プロジェクトをビルドし、拡張機能を Marketplace にアップロードします。 参照してください[Visual Studio 拡張機能を公開](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)します。 
    
> [!NOTE]
> 拡張機能パックをで使用できる拡張機能をインストールのみ、 [Visual Studio Marketplace](https://marketplace.visualstudio.com/)または[プライベート ギャラリー](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)します。
 
## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>Visual Studio Marketplace から拡張機能パックをインストールします。

これで、拡張機能を公開すると、Visual Studio にインストールし、テストします。

1. Visual Studio での**ツール** メニューのをクリックして**拡張機能と更新しています.**.

2. クリックして**オンライン**し検索`Test Extension Pack`します。

3. **[ダウンロード]** をクリックします。 拡張機能と拡張機能パックに含まれる拡張機能のリストは、インストールのスケジュールされます。

4. 以下のサンプル拡張機能パック ダウンロード ビューには、**拡張機能と更新**ダイアログ。 拡張の一覧を変更するには、拡張機能パックに含まれる拡張機能の一部のみをインストールする場合は、**インストールのスケジュールされた**します。

    ![Marketplace から拡張機能パックをダウンロードします。](media/vside-extensionpack.png)

5. インストールを完了するには、Visual Studio のすべてのインスタンスを閉じます。

## <a name="remove-the-extension"></a>拡張機能を削除します。

コンピューターから、拡張機能を削除します。

1. Visual Studio での**ツール** メニューのをクリックして**拡張機能と更新しています.**.

2. 選択`Test Extension Pack`し**アンインストール**します。 拡張機能と拡張機能パックに含まれる拡張機能のリストは、アンインストールのスケジュールされます。

3. アンインストールを完了するには、Visual Studio のすべてのインスタンスを閉じます。
