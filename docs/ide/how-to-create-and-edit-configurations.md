---
title: '方法: 構成を作成および編集する'
ms.date: 06/21/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- solution build configurations, editing
- build configurations, creating
- solution build configurations, creating
- build configurations, editing
- builds [Visual Studio], setting up
- property pages
- Configuration Manager
- project build configurations, creating
- project build configurations, editing
ms.assetid: 19be121c-148e-4ece-bbfc-d20b08cfc3f7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 949febb1b6d1aae01ae46b586721e1cf238549de
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55002048"
---
# <a name="how-to-create-and-edit-configurations"></a>方法: 構成を作成および編集する

ソリューションに対して、複数のビルド構成を作成することができます。 たとえば、問題を検出して修正するためにテスト担当者が使用できるデバッグ ビルドを構成できます。他にも、多様な顧客に配布できる多様な種類のビルドを構成できます。

> [!NOTE]
> このトピックは、Windows 上の Visual Studio に適用されます。 Visual Studio for Mac については、[Visual Studio for Mac でのビルド構成の作成と編集](/visualstudio/mac/create-and-edit-configurations)に関するページを参照してください。

## <a name="create-build-configurations"></a>ビルド構成を作成する

**[構成マネージャー]** ダイアログ ボックスを使用して、既存のビルド構成を選択または変更することも、新しい構成を作成することもできます。

**[構成マネージャー]** ダイアログ ボックスを開くには、**ソリューション エクスプローラー**でソリューションのショートカット メニューを開き、**[構成マネージャー]** を選択します。

> [!NOTE]
> **[構成マネージャー]** がショートカット メニューに表示されない場合は、メニュー バーの **[ビルド]** メニューを確認してください。 どちらにも表示されていない場合は、メニュー バーで **[ツール]** > **[オプション]** の順に選択します。次に、**[オプション]** ダイアログ ボックスの左ウィンドウで **[プロジェクトおよびソリューション]** > **[全般]** の順に展開し、右ウィンドウで **[ビルド構成の詳細を表示]** チェック ボックスをオンにします。

**[構成マネージャー]** ダイアログ ボックスでは、**[アクティブ ソリューション構成]** ボックスの一覧を使用して、ソリューション全体のビルド構成の選択、既存構成の変更、または新しい構成の作成を行うことができます。 **[アクティブ ソリューション プラットフォーム]** ドロップダウン リストを使用すると、構成の対象となるプラットフォームの選択、既存プラットフォームの変更、または新しいプラットフォームの追加を行うことができます。 **[プロジェクトのコンテキスト]** ウィンドウには、ソリューション内のプロジェクトが表示されます。 各プロジェクトについて、プロジェクト固有の構成とプラットフォームの選択、既存の構成とプラットフォームの変更、または新しい構成の作成あるいは新しいプラットフォームの追加を行うことができます。 また、ソリューション全体の構成を使用してソリューションをビルドまたは配置する際に、各プロジェクトを含めるかどうかをチェック ボックスで指定することができます。

 必要な構成を設定したら、その構成に適したプロジェクト プロパティを設定できます。

### <a name="to-set-properties-based-on-configurations"></a>構成に基づいてプロパティを設定するには

-   **ソリューション エクスプローラー**で、プロジェクトのショートカット メニューを開き、**[プロパティ]** を選択します。

     **[プロパティ ページ]** ウィンドウが開きます。

     構成に応じたプロパティを設定できます。 たとえば、リリース構成の場合、ソリューションのビルド時にコードを最適化することを指定できます。デバッグ構成の場合は、`DEBUG` 条件付きコンパイル シンボルを含むことを指定できます。 プロパティ ページの設定の詳細については、「[プロジェクトおよびソリューションのプロパティの管理](../ide/managing-project-and-solution-properties.md)」を参照してください。

## <a name="create-and-modify-project-configurations"></a>プロジェクト構成を作成および変更する

### <a name="to-create-a-project-configuration"></a>プロジェクト構成を作成するには

1.  **[構成マネージャー]** ダイアログ ボックスを開きます。

2.  **[プロジェクト]** 列でプロジェクトを選択します。

3.  そのプロジェクトの **[構成]** ボックスの一覧の **[新規作成]** をクリックします。

     **[新しいプロジェクト構成]** ダイアログ ボックスが表示されます。

4.  **[名前]** ボックスに、新しい構成の名前を入力します。

5.  既存のプロジェクト構成に指定されているプロパティ設定を使用するには、**[設定のコピー元]** ボックスの一覧から構成を選択します。

6.  ソリューション全体の構成を同時に作成するには、**[新しいソリューション構成を作成する]** チェック ボックスをオンにします。

### <a name="to-rename-a-project-configuration"></a>プロジェクト構成の名前を変更するには

1.  **[構成マネージャー]** ダイアログ ボックスを開きます。

2.  **[プロジェクト]** 列で、プロジェクト構成の名前を変更するプロジェクトを選択します。

3.  そのプロジェクトの **[構成]** ボックスの一覧の **[編集]** をクリックします。

     **[プロジェクト構成の編集]** ダイアログ ボックスが表示されます。

4.  変更するプロジェクト構成名を選択します。

5.  **[名前変更]** をクリックし、新しい名前を入力します。

## <a name="create-and-modify-solution-wide-build-configurations"></a>ソリューション全体のビルド構成を作成および変更する

### <a name="to-create-a-solution-wide-build-configuration"></a>ソリューション全体のビルド構成を作成するには

1.  **[構成マネージャー]** ダイアログ ボックスを開きます。

2.  **[アクティブ ソリューション構成]** ボックスの一覧で、**[新規作成]** をクリックします。

     **[新しいソリューション構成名]** ダイアログ ボックスが表示されます。

3.  **[名前]** ボックスに、新しい構成の名前を入力します。

4.  既存のソリューション構成に指定されている設定を使用するには、**[設定のコピー元]** ボックスの一覧から構成を選択します。

5.  プロジェクト構成を同時に作成するには、**[新しいプロジェクト構成を作成する]** チェック ボックスをオンにします。

### <a name="to-rename-a-solution-wide-build-configuration"></a>ソリューション規模のビルド構成の名前を変更するには

1.  **[構成マネージャー]** ダイアログ ボックスを開きます。

2.  **[アクティブ ソリューション構成]** ボックスで **[編集]** をクリックします。

     **[ソリューション構成の編集]** ダイアログ ボックスが表示されます。

3.  変更するソリューション構成名を選択します。

4.  **[名前変更]** をクリックし、新しい名前を入力します。

### <a name="to-modify-a-solution-wide-build-configuration"></a>ソリューション全体のビルド構成を変更するには

1.  **[構成マネージャー]** ダイアログ ボックスを開きます。

2.  **[アクティブ ソリューション構成]** ボックスの一覧で、構成を選択します。

3.  **[プロジェクトのコンテキスト]** ウィンドウで、すべてのプロジェクトに対して、必要な**構成**と**プラットフォーム**を選択し、**ビルド**するかどうかと、**配置**するかどうかを指定します。

## <a name="see-also"></a>関連項目

- [ビルド構成について](../ide/understanding-build-configurations.md)
- [Visual Studio でのプロジェクトとソリューションのビルドおよびクリーン](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [プロジェクトおよびソリューションのプロパティの管理](managing-project-and-solution-properties.md)
- [ビルド構成の作成と編集 (Visual Studio for Mac)](/visualstudio/mac/create-and-edit-configurations)