---
title: 設定を同期する
ms.date: 01/23/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 633767e66a4b3d976999574c885a3e6f7a06ddcf
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766130"
---
# <a name="synchronize-visual-studio-settings-across-multiple-computers"></a>複数のコンピューター間で Visual Studio 設定を同期する

複数のコンピューターで同じ個人アカウントを使用して Visual Studio にサインインした場合、コンピューター間で設定が同期されます。

## <a name="synchronized-settings"></a>同期された設定

既定では、次の設定が同期されます。

- 開発設定。 Visual Studio を初めて実行するときに設定を選択する必要がありますが、選択内容はいつでも変更できます。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。

- ユーザー定義のコマンド エイリアス。 コマンド エイリアスを定義する方法について詳しくは、「[Visual Studio コマンドの定義済みのエイリアス](../ide/reference/visual-studio-command-aliases.md)」をご覧ください。

- **[ウィンドウ]** > **[ウィンドウ レイアウトの管理]** ページのユーザー定義のウィンドウ レイアウト。

- **[ツール]** > **[オプション]** ページの次のオプション。

   - **[環境]** > **[全般]** オプション ページの [テーマ] とメニュー バー枠の設定。

   - **[環境]** > **[フォントおよび色]** オプション ページのすべての設定。

   - **[環境]** > **[キーボード]** オプション ページのすべてのキーボード ショートカット。

   - **[環境]** > **[タブとウィンドウ]** オプション ページのすべての設定。

   - **[環境]** > **[スタートアップ]** オプション ページのすべての設定。

   - **[テキスト エディター]** オプション ページのすべての設定。

   - **[XAML デザイナー]** オプション ページのすべての設定。

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>特定のコンピューター上の同期された設定の無効化

Visual Studio の同期された設定は、既定でオンになっています。 あるコンピューター上の同期された設定をオフにするには、**[ツール]** > **[オプション]** > **[環境]** > **[アカウント]** ページに移動して、**[Visual Studio にサインインしたときにデバイス間の設定を同期する]** チェック ボックスをオフにします。 たとえば、コンピューター "A" 上の Visual Studio の設定を同期しないようにすると、コンピューター "A" で行った設定変更がコンピューター "B" やコンピューター "C" に表示されなくなります。 コンピューター "B" と "C" は、引き続き相互に同期しますが、コンピューター "A" とは同期しなくなります。

## <a name="reset-settings"></a>リセット設定

次の手順で、すべての設定を既定に戻すことができます。

1. Visual Studio で、**[ツール]** > **[設定のインポートとエクスポート]** の順にクリックし、**設定のインポートとエクスポート ウィザード**を開始します。

1. **[設定のインポートとエクスポート]** で、**[すべての設定をリセット]**、**[次へ]** の順に選択します。

   ![Visual Studio の設定のインポートとエクスポート ウィザード](media/reset-all-settings.png)

1. **[現在の設定の保存]** ページで、**[はい]** または **[いいえ]** を選択し、**[次へ]** を選択します。

1. **[設定の既定のコレクションの選択]** ページで、コレクションを選択し、**[完了]** を選択します。

   ![Visual Studio の設定コレクション](media/settings-collections.png)

1. **[リセットの完了]** ページで **[閉じる]** を選択します。

## <a name="synchronize-settings-across-visual-studio-family-products-and-editions"></a>Visual Studio ファミリ製品およびエディション間での設定の同期

Community エディションを含む Visual Studio の任意のエディション間で、設定を同期できます。 Visual Studio ファミリ製品の間でも設定が同期されます。 ただし、各ファミリ製品には Visual Studio で共有されない独自の設定が含まれる場合があります。 たとえば、コンピューター "A" 上の 1 つの製品に固有の設定は、コンピューター "B" 上の別の製品と共有されますが、コンピューター "A" または "B" 上の Visual Studio とは共有されません。

## <a name="side-by-side-synchronized-settings"></a>サイド バイ サイドで同期された設定

Visual Studio 2017 バージョン 15.3 以降では、Visual Studio 2017 の異なるサイド バイ サイド インストールの間で、ツール ウィンドウ レイアウトなど、特定の設定が共有されません。 *%userprofile%\Documents\Visual Studio 2017\Settings* の *CurrentSettings.vssettings* ファイルはインストール固有フォルダーに置かれています。このフォルダーは、*%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx\Settings* のようなフォルダーになります。

> [!NOTE]
> 新しいインストール固有設定を使用するには、新しくインストールを行います。 既存の Visual Studio 2017 インストールを最新の更新プログラムにアップグレードするとき、既存の共有フォルダーが使用されます。

現在、Visual Studio 2017 がサイド バイ サイド インストールされているとき、新しいインストール固有設定ファイル用フォルダーを使用する場合、次の手順に従ってください。

1. Visual Studio 2017 バージョン 15.3 以降にアップグレードします。

1. **設定のインポート/エクスポート** ウィザードを利用し、すべての既存設定を *%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx* フォルダーから別の場所にエクスポートします。

1. アップグレードした Visual Studio で **VS 2017 用の開発者コマンド プロンプト**を開き、`devenv /resetuserdata` を実行します。

1. Visual Studio を起動し、エクスポートした設定ファイルから保存済みの設定をインポートします。

## <a name="see-also"></a>関連項目

[IDE をカスタマイズする](../ide/personalizing-the-visual-studio-ide.md)
