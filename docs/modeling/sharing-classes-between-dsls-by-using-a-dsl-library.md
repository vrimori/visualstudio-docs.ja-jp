---
title: DSL ライブラリによる DSL 間でのクラスの共有
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 32e699c88060949a7949fc19935137209b44e526
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55020620"
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>DSL ライブラリによる DSL 間でのクラスの共有
Visual Studio Visualization and Modeling SDK で別の DSL にインポートすることができます、不完全な DSL 定義を作成できます。 これにより、類似したモデルの共通部分を考慮することができます。

## <a name="creating-and-using-dsl-libraries"></a>DSL ライブラリの作成と

#### <a name="to-create-a-dsl-library"></a>DSL ライブラリを作成するには

1.  新しい DSL プロジェクトを作成し、DSL ライブラリのソリューション テンプレートを選択します。

     1 つの DSL プロジェクトが空のモデルで作成されます。

2.  ドメイン クラス、リレーションシップ、図形は、これに追加できます。

     ライブラリ内の要素は、1 つの埋め込みツリーを形成する必要はありません。

     インポーターを使用するリレーションシップを定義するには、2 つのドメイン クラスを作成し、それらの間のリレーションシップを作成します。

     設定を検討してください、**継承修飾子**ドメイン クラスの`Abstract`します。

3.  接続ビルダーなどの DSL のエクスプ ローラーで定義する要素を追加することができます。

4.  検証制約など、追加のコードが必要なカスタマイズを追加できます。

5.  クリックして**すべてのテンプレートの変換**します。

6.  プロジェクトをビルドします。

7.  使用するには、他のユーザーの DSL を配布するときに、コンパイル済みアセンブリ (DLL) とファイルの両方を提供する必要があります`DslDefinition.dsl`します。 下のフォルダーにコンパイルされたアセンブリを見つけることができます。 `Dsl\bin\*`

#### <a name="to-import-a-dsl-library"></a>DSL ライブラリをインポートするには

1. 別の DSL 定義内で**DSL エクスプ ローラー**、DSL のルート クラスを右クリックし、クリックして**新しい DslLibrary インポートの追加**します。

2. [プロパティ] ウィンドウで次のように設定します。、**ファイル パス**ライブラリ。 相対パスまたは絶対パスを使用することができます。

    インポートされたライブラリは、読み取り専用モードには、DSL エクスプ ローラーで表示されます。

3. 基底クラスとしてインポートされたクラスを使用することができます。 インポートの DSL のドメイン クラスを作成し、プロパティ ウィンドウで、設定**ベース クラス**をインポートするクラス。

4. すべてのテンプレートの変換 をクリックします。

5. DSL ライブラリのプロジェクトによってビルドされたアセンブリ (DLL) への参照を DSL プロジェクトに追加します。

6. ソリューションをビルドします。

   DSL ライブラリには、その他のライブラリをインポートできます。 ライブラリをインポートするときに、そのインポートは DSL エクスプ ローラーにも自動的に表示されます。

## <a name="see-also"></a>関連項目

- [方法: ドメイン固有言語を定義する](../modeling/how-to-define-a-domain-specific-language.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
