---
title: Visual Studio での設定の同期
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
ms.openlocfilehash: 91c8c931d71855913cdfaca4243711c917e3c8b4
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="synchronize-your-settings-in-visual-studio"></a>Visual Studio での設定の同期

複数のコンピューターで同じ個人アカウントを使用して Visual Studio にサインインした場合、既定ではすべてのコンピューターで設定が同期されます。

## <a name="synchronized-settings"></a>同期された設定

既定では、次の設定が同期されます。

- 開発設定 (Visual Studio を初めて実行するときに設定を選択する必要がありますが、選択内容はいつでも変更できます)。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。

- **[ツール]** > **[オプション]** ページの次のオプション。

    - **[環境]** > **[全般]** オプション ページの [テーマ] およびメニュー バー枠の設定

    - **[環境]** > **[フォントおよび色]** オプション ページのすべての設定

    - **[環境]** > **[キーボード]** オプション ページのすべてのキーボード ショートカット

    - **[環境]** > **[タブとウィンドウ]** オプション ページのすべての設定

    - **[環境]** > **[スタートアップ]** オプション ページのすべての設定

    - **[テキスト エディター]** オプション ページのすべての設定

    - **[XAML デザイナー]** オプション ページのすべての設定

- ユーザー定義のコマンド エイリアス。 コマンド エイリアスを定義する方法について詳しくは、「[Visual Studio コマンドの定義済みのエイリアス](../ide/reference/visual-studio-command-aliases.md)」をご覧ください。

- **[ウィンドウ]** > **[ウィンドウ レイアウトの管理]** ページのユーザー定義のウィンドウ レイアウト

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>特定のコンピューター上の同期された設定の無効化

Visual Studio の同期された設定は、既定でオンになっています。 あるコンピューター上の同期された設定をオフにするには、**[ツール]** > **[オプション]** > **[環境]** > **[アカウント]** ページに移動して、チェック ボックスをオフにします。  たとえば、コンピューター A 上の Visual Studio の設定を同期しないようにすると、コンピューター A で行った設定変更がコンピューター B やコンピューター C に表示されなくなります。コンピューター B および C は、引き続き相互に同期しますが、コンピューター A とは同期しなくなります。

## <a name="synchronize-settings-across-visual-studio-family-products-and-editions"></a>Visual Studio ファミリ製品およびエディション間での設定の同期

Community エディションを含む Visual Studio の任意のエディション間で、設定を同期できます。 Visual Studio ファミリ製品の間でも設定が同期されます。 ただし、各ファミリ製品には Visual Studio で共有されない独自の設定が含まれる場合があります。 たとえば、コンピューター A 上の 1 つの製品に固有の設定は、コンピューター B 上の別の製品と共有されますが、コンピューター A または B 上の Visual Studio では共有されません。

## <a name="side-by-side-synchronized-settings"></a>サイド バイ サイドで同期された設定

Visual Studio 15.3 以降では、*%userprofile%\Documents\Visual Studio 2017\Settings* にあった *CurrentSettings.vssettings* ファイルの場所をインストール専用フォルダー (例: *%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx\Settings*) に変更しました。この変更により、Visual Studio 2017 の横並びインストール間でツール ウィンドウ レイアウトのような特定の設定が共有されることがなくなりました。

> [!NOTE]
> 新しいインストールの設定を使用するには、新規インストールを完了する必要があります。 既存の Visual Studio 2017 インストールを最新の更新プログラムにアップグレードすると、既存の共有フォルダーが使用されます。 現在、Visual Studio 2017 がサイド バイ サイド インストールされているとき、アップグレードし、新しいインストールの設定ファイル用フォルダーを使用する場合、次の手順に従ってください。

1. アップグレード後、**設定のインポート/エクスポート** ウィザードを利用し、すべての既存設定を *%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx* フォルダーから別の場所にエクスポートします。
2. アップグレードした Visual Studio で **VS 2017 用の開発者コマンド プロンプト**を開き、そこから `devenv /resetuserdata` を実行します。
3. Visual Studio を起動し、エクスポートした設定ファイルから保存済みの設定をインポートします。

## <a name="see-also"></a>関連項目

[IDE をカスタマイズする](../ide/personalizing-the-visual-studio-ide.md)
