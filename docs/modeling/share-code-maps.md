---
title: エクスポートし、コード マップの保存
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- multiple
ms.openlocfilehash: a4f53f349b4bc2f578ad007761df32e5c4145dbc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54984497"
---
# <a name="share-code-maps"></a>コード マップの共有

コード マップは、Visual Studio プロジェクトの一部として、画像、または XPS ファイルとして保存できます。

## <a name="share-a-code-map-with-other-visual-studio-users"></a>コード マップを他の Visual Studio のユーザーと共有します。

マップを保存するには、 **[ファイル]** メニューを使用します。

- または -

マップのツールバーで、特定のプロジェクトの一部としてマップを保存する**共有** > **移動\<CodeMapName > に .dgml**、保存するプロジェクトを選択し、マップします。

![マップを別のプロジェクトに移動する](../modeling/media/codemapsmovemapmenu.png)

Visual Studio とのマップを保存する、 *.dgml*ファイルを Visual Studio Enterprise と Visual Studio Professional の他のユーザーと共有することができます。

> [!NOTE]
> Visual Studio Professional を使用するユーザーとマップを共有する前に、グループを展開しておくこと、非表示のノードとグループ間リンクを表示しておくこと、マップに表示する必要のある削除済みのノードを取得しておくことが必要です。 そうしない場合、他のユーザーはそれらの項目を表示できなくなります。
>
> モデリング プロジェクト内のマップまたはモデリング プロジェクトから別の場所にコピーされたマップを保存すると、次のエラーが発生する可能性があります。
>
> "プロジェクト ディレクトリの外部で *fileName* を保存できません。 リンクされた項目はサポートされていません。"
>
> Visual Studio にはエラーが表示されます。ただし、保存したバージョンは生成されます。 このエラーを回避するには、モデリング プロジェクトの外部でマップを生成します。 その後、目的の場所にグラフを保存できます。 単にソリューション内の別の場所にファイルをコピーし、その後で保存しようとすると失敗します。

## <a name="export-a-code-map-as-an-image"></a>コード マップをイメージとしてエクスポートします。

コード マップをイメージとしてエクスポートするときに、Microsoft Word や PowerPoint などの他のアプリケーションにコピーすることができます。

1. コード マップ ツールバーでは、次のように選択します。**共有** > **イメージとして電子メールで送信**または**イメージのコピー**します。

2. そのイメージを他のアプリケーションに貼り付けます。

## <a name="export-the-map-as-an-xps-file"></a>マップを XPS ファイルとしてエクスポートします。

コード マップを XPS ファイルとしてエクスポートするときに、Internet Explorer などの XML や XAML ビューアーで確認ができます。

1. コード マップ ツールバーでは、次のように選択します。**共有** > **ポータブル XPS として電子メール**または**ポータブル XPS として保存**します。

2. ファイルを保存する場所を参照します。

3. コード マップの名前を付けます。 確認、**型として保存**に設定されているボックス**XPS ファイル (\*.xps)** します。 **[保存]** をクリックします。

## <a name="see-also"></a>関連項目

- [コード マップで依存関係をマッピングします。](../modeling/map-dependencies-across-your-solutions.md)