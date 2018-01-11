---
title: "プロジェクトおよびソリューションのプロパティの管理 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5315dd07ab0c791cc9a349c08431ceb4a9b5c797
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="managing-project-and-solution-properties"></a>プロジェクトおよびソリューションのプロパティの管理

プロジェクトのプロパティでは、コンパイル、デバッグ、テストおよび配置の多くの側面を制御します。 プロジェクトのすべての種類に共通のプロパティや、特定の言語またはプラットフォームに固有のプロパティがあります。 プロジェクトのプロパティにアクセスするには、ソリューション エクスプローラーでプロジェクト ノードを右クリックして **[プロパティ]** を選択するか、メニュー バーの **[クイック起動]** 検索ボックスに「プロパティ」と入力します。

![プロジェクトのコンテキスト メニュー](../ide/media/vs2015_proj_prop_menu.gif "vs2015_proj_prop_menu")

.NET プロジェクトでは、プロジェクト ツリー自体にプロパティ ノードが含まれる場合もあります。

![ソリューション エクスプローラー ツリーの [プロパティ] ノード](../ide/media/vs2015_props_se.png "VS2015_Props_SE")

## <a name="project-properties"></a>プロジェクト プロパティ

プロジェクトのプロパティはグループに分類されており、グループごとに専用のプロパティ ページがあります。 ページは、言語およびプロジェクト タイプによって異なる場合があります。

### <a name="c-visual-basic-and-f-projects"></a>C# プロジェクト、Visual Basic プロジェクト、F# プロジェクト

C# プロジェクト、Visual Basic プロジェクト、F# プロジェクトでは、プロパティは**プロジェクト デザイナー**で公開されます。 C# の WPF プロジェクトの [ビルド] プロパティ ページを次の図に示します。

![Visual Studio プロジェクト デザイナー](../ide/media/vs2015_proppage_build.png "VS2015_PropPage_Build")

プロジェクト デザイナーのそれぞれのプロパティ ページについては、「[プロジェクト プロパティ リファレンス](../ide/reference/project-properties-reference.md)」を参照してください。

> [!TIP]
> ソリューションには少数のプロパティがあり、プロジェクト項目にも少数のプロパティがあります。これらのプロパティは、**プロジェクト デザイナー**ではなく、[[プロパティ] ウィンドウ](../ide/reference/properties-window.md)からアクセスします。

### <a name="c-and-javascript-projects"></a>C++ プロジェクトおよび JavaScript プロジェクト

C++ プロジェクトおよび JavaScript プロジェクトには、プロジェクトのプロパティを管理するために別のユーザー インターフェイスが用意されています。 この図は、C++ プロジェクトのプロパティ ページを示しています (JavaScript ページはほぼ同じです)。

![Visual C&#43;&#43; プロジェクトのプロパティ](../ide/media/vs2015_projprops_cpp.png "VS2015_ProjProps_cpp")

C++ プロジェクトのプロパティについては、[C++ プロジェクトのプロパティの操作](/cpp/ide/working-with-project-properties)に関するページをご覧ください。 JavaScript のプロパティの詳細については、「[プロパティ ページ、JavaScript](../ide/reference/property-pages-javascript.md)」を参照してください。

## <a name="solution-properties"></a>ソリューションのプロパティ

ソリューションのプロパティにアクセスするには、**ソリューション エクスプローラー**でソリューション ノードを右クリックし、**[プロパティ]** を選択します。 このダイアログでは、デバッグ ビルドまたはリリース ビルド用にプロジェクト構成を設定し、F5 キーを押した時点でのスタートアップ プロジェクトとなるプロジェクトを選択し、コード分析のオプションを設定します。

## <a name="see-also"></a>関連項目

[Visual Studio のソリューションおよびプロジェクト](../ide/solutions-and-projects-in-visual-studio.md)
