---
title: 1 つのソリューション内の複数の DSL
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: fce705b4f36c8c3bf0e6d44feaff353853652cb3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53940655"
---
# <a name="multiple-dsls-in-one-solution"></a>1 つのソリューション内の複数の DSL
いくつかの DSL を単一ソリューションの一部としてパッケージ化し、同時にインストールすることができます。

 複数の DSL を統合するためにいくつかの手法を使用できます。 詳細については、次を参照してください。 [Visual Studio modelbus によるモデルの統合](../modeling/integrating-models-by-using-visual-studio-modelbus.md)と[方法。ドラッグ アンド ドロップ ハンドラーを追加](../modeling/how-to-add-a-drag-and-drop-handler.md)と[コピー動作のカスタマイズ](../modeling/customizing-copy-behavior.md)します。

### <a name="to-build-more-than-one-dsl-in-the-same-solution"></a>複数の DSL を同じソリューションの中にビルドするには

1. 2 つ以上の DSL ソリューションと 1 つの VSIX プロジェクトを作成し、すべてのプロジェクトを単一のソリューションに追加します。

   -   新しい VSIX プロジェクトを作成するには**新しいプロジェクト**ダイアログ ボックスで、 **Visual c#**、**拡張**、 **VSIX プロジェクト**します。

   -   VSIX ソリューション ディレクトリ内に 2 つ以上の DSL ソリューションを作成します。

        各 DSL について、Visual Studio の新しいインスタンスを開きます。 新しい DSL を作成し、同じソリューション フォルダとして VSIX ソリューションを指定します。

        各 DSL は異なるファイル拡張子名を付けて作成します。

   -   名前を変更、 **Dsl**と**DslPackage**プロジェクトはすべて異なるようにします。 たとえば、`Dsl1`、`DslPackage1`、`Dsl2`、`DslPackage2` のようになります。

   -   各**DslPackage\*\source.extension.tt**、正しい Dsl プロジェクト名にこの行を更新します。

        `string dslProjectName = "Dsl2";`

   -   VSIX ソリューションで、Dsl * と DslPackage 追加\*プロジェクト。

        各ペアを独自のソリューション フォルダーに配置することを推奨します。

2. 以下のように DSL の VSIX マニフェストを結合します。

   1.  開いている_YourVsixProject_**\source.extension.manifest**します。

   2.  各 DSL は、選択**コンテンツの追加**を追加します。

       -   `Dsl*` プロジェクトとして、 **MEF コンポーネント**

       -   `DslPackage*` プロジェクトとして、 **MEF コンポーネント**

       -   `DslPackage*` プロジェクトとして、 **VS パッケージ**

3. ソリューションをビルドします。

   この結果の VSIX では両方の DSL がインストールされます。 F5 キーを使用してテストするしたり展開したり_YourVsixProject_**\bin\Debug\\\*.vsix**します。

## <a name="see-also"></a>関連項目

- [Visual Studio Modelbus によるモデルの統合](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [方法: ドラッグ アンド ドロップ ハンドラーを追加します。](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [コピー動作のカスタマイズ](../modeling/customizing-copy-behavior.md)