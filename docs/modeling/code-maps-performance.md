---
title: コード マップが遅い
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- multiple
ms.openlocfilehash: ebdd8809ed4c9ad7079cecd8f28986eb711bc304
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54981296"
---
# <a name="improve-performance-for-code-maps"></a>コード マップのパフォーマンスを向上させる

マップを初めて生成したときに、Visual Studio は、見つかったすべての依存関係のインデックスを作成します。 このプロセスは、大規模なソリューションは、特に、しばらく時間がかかる場合がありますが、後でパフォーマンスが向上します。 コードが変更された場合、Visual Studio では、更新されたコードだけにインデックスが付け直されます。 マップのレンダリングを完了するのにかかる時間を最小限に抑えるには、次の推奨事項を考慮してください。

- [目的の依存関係のみをマップする。](#create-a-code-map-to-see-specific-dependencies)

- ソリューション全体のマップを生成する前に、ソリューションのスコープを縮小する。

- 選択して、自動ビルド、ソリューションをオフにする**ビルドのスキップ**コード マップのツールバー。

- 選択して、親項目の自動追加をオフに**親を含める**コード マップのツールバー。

   ![[ビルドのスキップ] ボタンと [親を含める] ボタン](../modeling/media/codemapsfilterskipbuildicons.png)

- コード マップ ファイルを直接編集し、不要なノードとリンクを削除する。 マップを変更しても、基のコードには影響しません。 「 [DGML ファイルを編集してコード マップをカスタマイズする](../modeling/customize-code-maps-by-editing-the-dgml-files.md)」を参照してください。

マップを作成またはからのマップに項目を追加するための多くの時間がかかる場合があります**ソリューション エクスプ ローラー**プロジェクト項目の**出力ディレクトリにコピー**プロパティに設定されて**常にコピー**します。 パフォーマンスを向上させるには、このプロパティを **[新しい場合はコピーする]** または `PreserveNewest`に変更します。 参照してください[インクリメンタル ビルド](../msbuild/incremental-builds.md)します。

完成したマップは、正常にビルドされたコードに対してのみの依存関係を示します。 特定のコンポーネントにビルド エラーが発生すると、そのエラーがマップに表示されます。 マップに基づいてアーキテクチャを決定する前に、コンポーネントが実際にビルドされ、その依存関係がマップ上に表示されていることを確認してください。