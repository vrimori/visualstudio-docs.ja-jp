---
title: "Visual Studio のインストールに使用するコマンド ライン パラメーターの例 | Microsoft Docs"
ms.custom: 
ms.date: 04/05/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
author: timsneath
ms.author: tims
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 4e33dc3ebb32569b547aa9bcb6db9a15dbe4fc21
ms.openlocfilehash: ff67313f350264b39151bc0e2f7191ab16300f24
ms.lasthandoff: 04/05/2017

---
# <a name="command-line-parameter-examples-for-visual-studio-2017-installation"></a>Visual Studio 2017 のインストールに使用するコマンド ライン パラメーターの例
[コマンド ライン パラメーターを使用して Visual Studio をインストールする](use-command-line-parameters-to-install-visual-studio.md)方法を説明するため、いくつかの例を以下に示します。例は必要に応じてカスタマイズできます。

それぞれの例で、`vs_enterprise.exe`、`vs_professional.exe`、`vs_community.exe` は Visual Studio ブートストラップの各エディションを表します。ブートストラップは、ダウンロード プロセスを開始する (約 1 MB の) 小さいファイルです。 別のエディションを使用している場合は、適切なブートス トラップの名前に置き換えてください。

> [!NOTE]
> すべてのコマンドは、管理者特権で実行する必要があり、管理者のプロンプトからプロセスが開始されていない場合は、ユーザー アカウント制御の確認メッセージが表示されます。

* 対話型プロンプトを使用せず、進行状況を表示して、Visual Studio の最小限のインスタンスをインストールする例です。
```cmd
vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
```

* フランス語の言語パックを使用する Visual Studio のデスクトップ インスタンスをサイレント モードでインストールする例です。製品のインストールが終わるまでダイアログは表示されません。
```cmd
vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --quiet --wait
```

  > [!NOTE]
  >  `--wait` パラメーターはバッチ ファイル用に設計されています。 バッチ ファイルでは、インストールが完了するまで次のコマンドの実行は続行されません。 `%ERRORLEVEL%` 環境変数にはコマンドの戻り値が格納されます (「[コマンド ライン パラメーターを使用して Visual Studio をインストールする](use-command-line-parameters-to-install-visual-studio.md)」のページを参照)。

* .NET デスクトップおよび .NET Web ワークロード、すべての推奨コンポーネント、GitHub 拡張機能をダウンロードする例です。 英語の言語パックのみを組み込みます。
```cmd
vs_community.exe --layout C:\VS2017
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Microsoft.Net.ComponentGroup.TargetingPacks.Common ^
   --add Microsoft.ComponentGroup.Blend ^
   --add Microsoft.VisualStudio.Component.EntityFramework ^
   --add Microsoft.VisualStudio.Component.DiagnosticTools ^
   --add Microsoft.VisualStudio.Component.DockerTools ^
   --add Microsoft.VisualStudio.Component.CloudExplorer ^
   --add Microsoft.VisualStudio.Component.Wcf.Tooling ^
   --add Component.GitHub.VisualStudio
```

   >[!NOTE]
   Enterprise Edition には、この例に示されているもの以外に追加の推奨コンポーネントが含まれています。 Visual Studio Enterprise で利用できるすべての推奨コンポーネントの一覧を確認するには、「[Visual Studio Enterprise 2017 のコンポーネント ディレクトリ](workload-component-id-vs-enterprise.md)」を参照してください。

* Visual Studio 2017 Enterprise Edition で利用できるすべてのワークロードとコンポーネントの対話型インストールを開始します。
```cmd
vs_enterprise.exe --all --includeRecommended --includeOptional
```

* Visual Studio 2017 Community Edition が既にインストールされているコンピューターに、Visual Studio 2017 Professional の 2 つ目の名前付きインスタンスを Node.js 開発のサポートとともにインストールします。
```cmd
vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --nickname VSforNode
```

* 既定のインストール済み Visual Studio のインスタンスからプロファイリング ツール コンポーネントを削除します。
```cmd
vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
```

  > [!NOTE]
  >  コマンド ラインの末尾で `^` 文字を使用すると、複数行を連結して 1 行にすることができます。 または、これらのコマンドを単純に 1 つの行に配置できます。

## <a name="see-also"></a>関連項目

 * [Visual Studio 管理者ガイド](visual-studio-administrator-guide.md)
 * [コマンド ライン パラメーターを使用して Visual Studio をインストールする](use-command-line-parameters-to-install-visual-studio.md)
 * [Visual Studio 2017 のオフライン インストールを作成する](create-an-offline-installation-of-visual-studio.md)

