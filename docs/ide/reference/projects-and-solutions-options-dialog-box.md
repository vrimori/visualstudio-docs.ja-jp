---
title: '[プロジェクトおよびソリューション] の [オプション] ダイアログ ボックス'
ms.date: 07/14/2017
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.General
- VS.ToolsOptionsPages.Projects.Locations
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 466df9ad82ef4bdc4b4cb3d699b53c0568f3b08a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53926314"
---
# <a name="projects-and-solutions-page-options-dialog-box"></a>[プロジェクトおよびソリューション] ページの [オプション] ダイアログ ボックス

プロジェクトおよびソリューションに関連する Visual Studio の動作を設定します。 これらのオプションにアクセスするには、**[ツール]**、**[オプション]** の順に選択し、**[プロジェクトおよびソリューション]** を展開し、**[全般]** をクリックします。

プロジェクトおよびテンプレート フォルダーの既定のパスは、同じダイアログ ボックスの **[場所]** タブで設定します。

## <a name="general-page"></a>[全般] ページ

**[全般]** ページで使用できるオプションは次のとおりです。

### <a name="always-show-error-list-if-build-finishes-with-errors"></a>ビルドがエラーで終了した場合には常にエラー一覧を表示する

プロジェクトのビルドが失敗した場合にのみ、ビルドの完了時に **[エラー一覧]** ウィンドウを開きます。 ビルド処理中に発生したエラーが表示されます。 このオプションがオフの場合、エラーは引き続き発生しますが、ビルドの完了時にウィンドウは開きません。 既定では、このオプションは有効になっています。

### <a name="track-active-item-in-solution-explorer"></a>ソリューション エクスプローラーでアクティブなアイテムを追跡する

選択した場合、**ソリューション エクスプローラー**が自動的に開いて、アクティブな項目が選択されます。 選択される項目は、プロジェクトまたはソリューション内の別のファイルや、デザイナー内の異なるコンポーネントを処理の対象にすると変更されます。 このオプションがオフのとき、**ソリューション エクスプローラー**での選択内容は自動的に変更されません。 既定では、このオプションは有効になっています。

### <a name="show-advanced-build-configurations"></a>ビルド構成の詳細を表示

選択した場合、ビルドの構成オプションが **[プロジェクト プロパティ ページ]** ダイアログ ボックスおよび **[ソリューション プロパティ ページ]** ダイアログ ボックスに表示されます。 オフにすると、ビルドの構成オプションは、1 つの構成または 2 つの構成のデバッグとリリースを含む Visual Basic および C# プロジェクトのための、**[プロジェクト プロパティ ページ]** ダイアログ ボックスや **[ソリューション プロパティ ページ]** ダイアログ ボックスに表示されません。 プロジェクトにユーザー定義の構成がある場合、ビルドの構成オプションが表示されます。

オフの場合、**[ビルド]** メニューのコマンド (**[ソリューションのビルド]**、**[ソリューションのリビルド]**、**[ソリューションのクリーン]** など) はリリース構成で実行され、**[デバッグ]** メニューのコマンド (**[デバッグ開始]**、**[デバッグなしで開始]** など) はデバッグ構成で実行されます。

### <a name="always-show-solution"></a>常にソリューションを表示

選択した場合、ソリューションおよびソリューションで動作するすべてのコマンドが常に IDE に表示されます。 オフの場合、すべてのプロジェクトはスタンドアロン プロジェクトとして作成され、ソリューションに 1 つのプロジェクトだけが含まれている場合、ソリューション エクスプローラー内のソリューションや、IDE 内のソリューションで動作するコマンドは表示されません。

### <a name="save-new-projects-when-created"></a>新しいプロジェクトを作成時に保存する

選択すると、**[新しいプロジェクト]** ダイアログ ボックスにプロジェクトの場所を指定できます。 オフの場合、すべての新しいプロジェクトは一時プロジェクトとして作成されます。 一時プロジェクトで作業する場合、ディスクの場所を指定しなくても、プロジェクトを作成して試してみることができます。

### <a name="warn-user-when-the-project-location-is-not-trusted"></a>プロジェクトの場所が信頼されていないときにユーザーに警告

完全に信頼されていない場所 (UNC パスの上や HTTP パスの上など) で、新しいプロジェクトの作成または既存のプロジェクトのオープンを試行すると、メッセージが表示されます。 このオプションを使用して、完全に信頼されていない場所でプロジェクトの作成またはオープンを試行するたびにメッセージを表示するかどうかを指定します。

### <a name="show-output-window-when-build-starts"></a>ビルド開始時に出力ウィンドウを表示

ソリューション ビルドの開始時に、IDE の[出力ウィンドウ](../../ide/reference/output-window.md)を自動的に表示します。

### <a name="prompt-for-symbolic-renaming-when-renaming-files"></a>ファイル名の変更時にシンボルの名前変更を求めるプロンプトを出す

選択すると、Visual Studio がコード要素に対するプロジェクト内のすべての参照も名前変更するかどうかを確認する、メッセージ ボックスが表示されます。

### <a name="prompt-before-moving-files-to-a-new-location"></a>Prompt before moving files to a new location\(新しい場所にファイルを移動する前にメッセージを表示する\)

選択すると、Visual Studio は、**ソリューション エクスプローラー**での操作によってファイルの場所が変更される前に確認メッセージ ボックスを表示します。

### <a name="reopen-documents-on-solution-load"></a>ソリューションの読み込み時にドキュメントを再度開く

**Visual Studio 2017 バージョン 15.8 プレビュー 2 以降の新機能**

オンにすると、前にこのソリューションを閉じたときに開かれていたドキュメントが、ソリューションを読み込むときに自動的に開かれます。

特定の種類のファイルまたはデザイナーを開きなおすと、ソリューションの読み込みが遅くなることがあります。 ソリューションの以前のコンテキストを復元する必要がない場合は、このオプションをオフにすると、[ソリューションの読み込みのパフォーマンス](../../ide/visual-studio-performance-tips-and-tricks.md#disable-automatic-file-restore)が向上します。

## <a name="locations-page"></a>[場所] タブ

**[場所]** ページで使用できるオプションは次のとおりです。

### <a name="projects-location"></a>プロジェクトの場所

Visual Studio が新しいプロジェクトとソリューション フォルダーを作成する既定の場所を指定します。 複数のダイアログ ボックスも、このオプションで指定した場所をフォルダーの開始点として使用します。 たとえば、**[プロジェクトを開く]** ダイアログ ボックスは、この場所を **[マイ プロジェクト]** のショートカットのために使用します。

### <a name="user-project-templates-location"></a>ユーザー プロジェクト テンプレートの場所

**[新しいプロジェクト]** ダイアログ ボックスで **[マイ テンプレート]** の一覧を作成するときに使用される既定の場所を指定します。 詳細については、「[方法 :テンプレートを配置して整理する](../../ide/how-to-locate-and-organize-project-and-item-templates.md)」を参照してください。

### <a name="user-item-templates-location"></a>ユーザー項目テンプレートの場所

**[新しい項目の追加]** ダイアログ ボックスで **[マイ テンプレート]** の一覧を作成するときに使用される既定の場所を設定します。 詳細については、「[方法 :テンプレートを配置して整理する](../../ide/how-to-locate-and-organize-project-and-item-templates.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [[オプション] ダイアログ ボックス、[プロジェクトおよびソリューション]、[ビルド/実行]](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [[オプション] ダイアログ ボックス、[プロジェクトおよびソリューション]、[Web プロジェクト]](../../ide/reference/options-dialog-box-projects-and-solutions-web-projects.md)
