---
title: インストールに使用するコマンド ライン パラメーターの例
description: これらの例をカスタマイズして、Visual Studio の独自のコマンド ライン インストールを作成します。
ms.date: 01/16/2019
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f407d1465211962743c51e0241f03cd25f5d5ca5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992166"
---
# <a name="command-line-parameter-examples-for-visual-studio-2017-installation"></a>Visual Studio 2017 のインストールに使用するコマンド ライン パラメーターの例

[コマンド ライン パラメーターを使用して Visual Studio をインストールする](use-command-line-parameters-to-install-visual-studio.md)方法を説明するため、いくつかの例を以下に示します。例は必要に応じてカスタマイズできます。

それぞれの例で、`vs_enterprise.exe`、`vs_professional.exe`、`vs_community.exe` は Visual Studio ブートストラップの各エディションを表します。ブートストラップは、ダウンロード プロセスを開始する (約 1 MB の) 小さいファイルです。 別のエディションを使用している場合は、適切なブートス トラップの名前に置き換えてください。

> [!NOTE]
> すべてのコマンドは、管理者特権で実行する必要があり、管理者のプロンプトからプロセスが開始されていない場合は、ユーザー アカウント制御の確認メッセージが表示されます。
>
> [!NOTE]
> コマンド ラインの末尾で `^` 文字を使用すると、複数行を連結して 1 行にすることができます。 または、これらのコマンドを単純に 1 つの行に配置できます。 PowerShell の場合、バッククォート (`` ` ``) 文字がこれに相当します。

コマンドラインを使用してインストールできるワークロードとコンポーネントの一覧は、「[Visual Studio のワークロード ID とコンポーネント ID](workload-and-component-ids.md)」ページをご覧ください。

## <a name="using---installpath"></a>Using --installPath

* 対話型プロンプトを使用せず、進行状況を表示して、Visual Studio の最小限のインスタンスをインストールする例です。

  ```cmd
  vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
  ```

* コマンド ラインを使用して Visual Studio インスタンスを更新すると、対話型のプロンプトは表示されませんが、進行状況が表示されます。

  ```cmd
  vs_enterprise.exe --update --quiet --wait
  vs_enterprise.exe update --wait --passive --norestart --installPath "C:\installPathVS"
  ```

  > [!NOTE]
  > 両方のコマンドが必要です。 最初のコマンドにより Visual Studio インストーラーが更新されます。 2 つめのコマンドにより Visual Studio インスタンスが更新されます。 ユーザー アカウント制御ダイアログが表示されないようにするには、管理者としてコマンド プロンプトを実行します。

* フランス語の言語パックを使用する Visual Studio のデスクトップ インスタンスをサイレント モードでインストールする例です。製品のインストールが終わるまでダイアログは表示されません。

  ```cmd
  vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended --quiet --wait
  ```

  > [!NOTE]
  > `--wait` パラメーターはバッチ ファイル用に設計されています。 バッチ ファイルでは、インストールが完了するまで次のコマンドの実行は続行されません。 `%ERRORLEVEL%` 環境変数にはコマンドの戻り値が格納されます (「[コマンド ライン パラメーターを使用して Visual Studio をインストールする](use-command-line-parameters-to-install-visual-studio.md)」のページを参照)。

## <a name="using---layout"></a>Using --layout

* Visual Studio コア エディター (最小 Visual Studio 構成) をダウンロードします。 英語の言語パックのみを組み込みます。

  ```cmd
  vs_community.exe --layout C:\VS2017
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
  ```

* .NET デスクトップおよび .NET Web ワークロード、すべての推奨コンポーネント、GitHub 拡張機能をダウンロードする例です。 英語の言語パックのみを組み込みます。

  ```cmd
  vs_community.exe --layout C:\VS2017 ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Component.GitHub.VisualStudio ^
   --includeRecommended
  ```

## <a name="using---all"></a>Using --all

* Visual Studio 2017 Enterprise Edition で利用できるすべてのワークロードとコンポーネントの対話型インストールを開始します。

  ```cmd
  vs_enterprise.exe --all
  ```

## <a name="using---includerecommended"></a>Using --includeRecommended

* Visual Studio 2017 Community Edition が既にインストールされているコンピューターに、Visual Studio 2017 Professional の 2 つ目の名前付きインスタンスを Node.js 開発のサポートとともにインストールします。

  ```cmd
  vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
  ```

## <a name="using---remove"></a>Using --remove

* 既定のインストール済み Visual Studio のインスタンスからプロファイリング ツール コンポーネントを削除します。

  ```cmd
  vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

## <a name="using---path"></a>Using --path

これらのコマンドライン パラメーターは **15.7 の新機能**です。 詳細については、[コマンドライン パラメーターを使用した Visual Studio のインストール](use-command-line-parameters-to-install-visual-studio.md)に関するページをご覧ください。

* install、cache、shared パスを使用:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache" --path shared="C:\VS\shared"`

* install パスと cache パスのみを使用:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache"`

* install パスと shared パスのみを使用:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path shared="C:\VS\shared"`

* install パスのみを使用:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS"`

## <a name="using-export"></a>export の使用

このコマンド ライン コマンドは、**15.9 の新機能**です。 詳細については、[コマンド ライン パラメーターを使用した Visual Studio のインストール](use-command-line-parameters-to-install-visual-studio.md)に関するページを参照してください。

* export を使用して、インストールの選択内容を保存します。

```cmd
"C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --installPath "C:\VS" --config "C:\.vsconfig"
```

* export を使用して、ゼロからカスタムの選択内容を保存します。

```cmd
"C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --config "C:\.vsconfig"
```

## <a name="using---config"></a>--config の使用

このコマンド ライン パラメーターは、**15.9 の新機能**です。 詳細については、[コマンド ライン パラメーターを使用した Visual Studio のインストール](use-command-line-parameters-to-install-visual-studio.md)に関するページを参照してください。

* --config を使用して、以前に保存したインストール構成ファイルからワークロードとコンポーネントをインストールします。

```cmd
vs_enterprise.exe --config "C:\.vsconfig" --installPath "C:\VS"
```

* --config を使用して、既存のインストールにワークロードとコンポーネントを追加します。

```cmd
vs_enterprise.exe modify --installPath "C:\VS" --config "C:\.vsconfig"
```


[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>関連項目

* [Visual Studio 管理者ガイド](visual-studio-administrator-guide.md)
* [コマンド ライン パラメーターを使用して Visual Studio をインストールする](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio 2017 のオフライン インストールを作成する](create-an-offline-installation-of-visual-studio.md)
* [Visual Studio のワークロードとコンポーネント ID](workload-and-component-ids.md)
