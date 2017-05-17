---
title: "Visual Studio のインストールに使用するコマンド ライン パラメーターの例 | Microsoft Docs"
ms.custom: 
ms.date: 05/06/2017
ms.reviewer: tims
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 0f07824b29e7851e353d472838a897853e227d6c
ms.contentlocale: ja-jp
ms.lasthandoff: 05/09/2017

---
# <a name="command-line-parameter-examples-for-visual-studio-2017-installation"></a>Visual Studio 2017 のインストールに使用するコマンド ライン パラメーターの例
[コマンド ライン パラメーターを使用して Visual Studio をインストールする](use-command-line-parameters-to-install-visual-studio.md)方法を説明するため、いくつかの例を以下に示します。例は必要に応じてカスタマイズできます。

それぞれの例で、`vs_enterprise.exe`、`vs_professional.exe`、`vs_community.exe` は Visual Studio ブートストラップの各エディションを表します。ブートストラップは、ダウンロード プロセスを開始する (約 1 MB の) 小さいファイルです。 別のエディションを使用している場合は、適切なブートス トラップの名前に置き換えてください。

> [!NOTE]
> すべてのコマンドは、管理者特権で実行する必要があり、管理者のプロンプトからプロセスが開始されていない場合は、ユーザー アカウント制御の確認メッセージが表示されます。

> [!NOTE]
>  コマンド ラインの末尾で `^` 文字を使用すると、複数行を連結して 1 行にすることができます。 または、これらのコマンドを単純に 1 つの行に配置できます。 PowerShell の場合、バッククォート (`` ` ``) 文字がこれに相当します。 

* 対話型プロンプトを使用せず、進行状況を表示して、Visual Studio の最小限のインスタンスをインストールする例です。
```
vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
```

* フランス語の言語パックを使用する Visual Studio のデスクトップ インスタンスをサイレント モードでインストールする例です。製品のインストールが終わるまでダイアログは表示されません。
```
vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended --quiet --wait
```

> [!NOTE]
>  `--wait` パラメーターはバッチ ファイル用に設計されています。 バッチ ファイルでは、インストールが完了するまで次のコマンドの実行は続行されません。 `%ERRORLEVEL%` 環境変数にはコマンドの戻り値が格納されます (「[コマンド ライン パラメーターを使用して Visual Studio をインストールする](use-command-line-parameters-to-install-visual-studio.md)」のページを参照)。

* Visual Studio コア エディター (最小 Visual Studio 構成) をダウンロードします。 英語の言語パックのみを組み込みます。

```cmd
vs_community.exe --layout C:\VS2017
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
```

* .NET デスクトップおよび .NET Web ワークロード、すべての推奨コンポーネント、GitHub 拡張機能をダウンロードする例です。 英語の言語パックのみを組み込みます。
```
vs_community.exe --layout C:\VS2017 ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Component.GitHub.VisualStudio ^
   --includeRecommended
```

* Visual Studio 2017 Enterprise Edition で利用できるすべてのワークロードとコンポーネントの対話型インストールを開始します。
```
vs_enterprise.exe --all --includeRecommended --includeOptional
```

* Visual Studio 2017 Community Edition が既にインストールされているコンピューターに、Visual Studio 2017 Professional の 2 つ目の名前付きインスタンスを Node.js 開発のサポートとともにインストールします。
```
vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
```

* 既定のインストール済み Visual Studio のインスタンスからプロファイリング ツール コンポーネントを削除します。
```
vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
```

## <a name="see-also"></a>関連項目

 * [Visual Studio 管理者ガイド](visual-studio-administrator-guide.md)
 * [コマンド ライン パラメーターを使用して Visual Studio をインストールする](use-command-line-parameters-to-install-visual-studio.md)
 * [Visual Studio 2017 のオフライン インストールを作成する](create-an-offline-installation-of-visual-studio.md)

