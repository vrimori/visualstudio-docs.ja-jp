---
title: コード マップは低速
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 2dece1e63fffdba67678422ad9241babc63b7abd
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="improve-performance-for-code-maps"></a>コード マップのパフォーマンスを向上させる

マップを初めて生成したときに、Visual Studio は、見つかったすべての依存関係のインデックスを作成します。 この処理は、大規模なソリューションは、特に、時間がかかる可能性がありますが、後でパフォーマンスが向上します。 コードが変更された場合、Visual Studio では、更新されたコードだけにインデックスが付け直されます。 マップのレンダリングを完了するのにかかった時間を最小限に抑えるには、以下の推奨事項を考慮してください。

- [関心のある依存関係のみをマップします。](#create-a-code-map-to-see-specific-dependencies)

- ソリューション全体のマップを生成する前に、ソリューションのスコープを縮小する。

- 選択して、ソリューションの自動ビルドをオフにする**ビルドのスキップ**コード マップ ツールバーでします。

- 選択して、親項目の自動追加をオフにする**親を含める**コード マップ ツールバーでします。

   ![[ビルドのスキップ] ボタンと [親を含める] ボタン](../modeling/media/codemapsfilterskipbuildicons.png)

- コード マップ ファイルを直接編集し、不要なノードとリンクを削除する。 マップを変更しても、基のコードには影響しません。 「 [DGML ファイルを編集してコード マップをカスタマイズする](../modeling/customize-code-maps-by-editing-the-dgml-files.md)」を参照してください。

マップを作成またはからのマップに項目を追加するための多くの時間がかかる場合があります**ソリューション エクスプ ローラー**プロジェクト項目の**出力ディレクトリにコピー**プロパティに設定されている**常にコピー**です。 パフォーマンスを向上させるには、このプロパティを **[新しい場合はコピーする]** または `PreserveNewest`に変更します。 参照してください[インクリメンタル ビルド](../msbuild/incremental-builds.md)です。

完成したマップは、正常に作成したコードにのみ依存関係を示します。 特定のコンポーネントにビルド エラーが発生すると、そのエラーがマップに表示されます。 マップに基づいてアーキテクチャを決定する前に、コンポーネントが実際にビルドされ、その依存関係がマップ上に表示されていることを確認してください。