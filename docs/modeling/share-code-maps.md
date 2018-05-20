---
title: エクスポートし、コード マップの保存
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: abfe8d6160d023a99e9a49480baada9acb0c8243
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="share-code-maps"></a>コード マップの共有

コード マップは、Visual Studio プロジェクトの一部として、画像、または XPS ファイルとして保存できます。

## <a name="share-a-code-map-with-other-visual-studio-users"></a>コード マップを他の Visual Studio ユーザーと共有します。

マップを保存するには、 **[ファイル]** メニューを使用します。

- または -

マップ ツールバーで、特定のプロジェクトの一部としてマップを保存する**共有** > **移動\<CodeMapName > に .dgml**、保存するプロジェクトを選択し、マップします。

![マップを別のプロジェクトに移動する](../modeling/media/codemapsmovemapmenu.png)

Visual Studio には、として、マップが保存され、 *.dgml*ファイルを他の Visual Studio Enterprise および Visual Studio Professional ユーザーと共有することができます。

> [!NOTE]
> Visual Studio Professional を使用するユーザーとマップを共有する前に、グループを展開しておくこと、非表示のノードとグループ間リンクを表示しておくこと、マップに表示する必要のある削除済みのノードを取得しておくことが必要です。 そうしない場合、他のユーザーはそれらの項目を表示できなくなります。
>
> モデリング プロジェクト内のマップまたはモデリング プロジェクトから別の場所にコピーされたマップを保存すると、次のエラーが発生する可能性があります。
>
> "プロジェクト ディレクトリの外部で *fileName* を保存できません。 リンクされた項目はサポートされていません。"
>
> Visual Studio にはエラーが表示されます。ただし、保存したバージョンは生成されます。 このエラーを回避するには、モデリング プロジェクトの外部でマップを生成します。 その後、目的の場所にグラフを保存できます。 単にソリューション内の別の場所にファイルをコピーし、その後で保存しようとすると失敗します。

## <a name="export-a-code-map-as-an-image"></a>コード マップをイメージとしてエクスポートします。

コード マップをイメージとしてエクスポートするときに、Microsoft Word や PowerPoint など、他のアプリケーションにコピーできます。

1. コード マップ ツールバーでは、次のように選択します。**共有** > **画像として電子メールで送信**または**イメージのコピー**です。

2. そのイメージを他のアプリケーションに貼り付けます。

## <a name="export-the-map-as-an-xps-file"></a>マップを XPS ファイルとしてエクスポートします。

コード マップを XPS ファイルとしてエクスポートするときに、Internet Explorer などの XML や XAML ビューアーで表示できます。

1. コード マップ ツールバーでは、次のように選択します。**共有** > **ポータブル XPS として電子メール**または**ポータブル XPS として保存**です。

2. ファイルを保存する場所を参照します。

3. コード マップの名前を付けます。 確認して、**型として保存**に設定されているボックス**XPS ファイル (\*.xps)** です。 **[保存]** をクリックします。

## <a name="see-also"></a>関連項目

- [コード マップと依存関係をマッピングします。](../modeling/map-dependencies-across-your-solutions.md)