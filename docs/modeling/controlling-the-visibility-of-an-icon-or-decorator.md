---
title: アイコンまたはデコレーターの可視性の制御
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 070f49b09086d463a13470f389a4857225b7add9
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2018
---
# <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>アイコンまたはデコレーターの可視性の制御
A*デコレータ*がアイコンまたはドメイン固有言語 (DSL) 内の図形に表示されるテキストの行。 デコレーターの表示を作成し、モデルのプロパティの状態によって非表示できます。 たとえば、人物を表す図形を使用して、個人の性別、子供の数に応じて表示されるアイコンが異なることができます。

## <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>アイコンまたはデコレーターの可視性を制御します。
 次の手順では、既に定義した図形およびそのマッピング ドメイン クラスを前提としています。 詳細については、次を参照してください。[ドメイン固有言語の定義方法](../modeling/how-to-define-a-domain-specific-language.md)です。

#### <a name="to-control-the-visibility-of-an-icon-or-text-decorator"></a>アイコンやテキスト デコレーターの可視性を制御するには

1.  DSL 定義ダイアグラムでは、アイコンまたは表示するテキスト デコレーター図形クラスに追加します。

    1.  図形のクラスを右クリックし、**追加**デコレーターの必要な型をクリックします。

    2.  デコレーターの設定**位置**プロパティです。 1 つ以上のデコレータの位置が、ことができます。 たとえば、male および female の位置が、共有のアイコンことができます。

    3.  設定、**アイコンの既定の**アイコン デコレーターのプロパティです。

2.  灰色の線は DSL 定義ダイアグラムで図形クラスと、ドメインであるダイアグラム要素のマップを選択します。

3.  DSL 詳細 ウィンドウで、**デコレータ マップ** タブで、デコレータを選択します。 たとえば、MaleDecorator です。

4.  チェック、**可視性フィルター**ボックス。

5.  可視性を制御する必要がありますの domain プロパティがオンの場合、即時のドメイン クラスのままにして**フィルター プロパティへのパス**空白。

     それ以外の場合、ドロップダウン メニューをクリックし、リレーションシップ、またはプロパティが配置されているクラスに移動します。

    -   エラー報告を避けるためには、する必要がありますいない内を移動するリレーションシップでマークされた"*"ナビゲーション ツールでします。

6.  設定、**フィルター プロパティ**ドメイン プロパティにします。 たとえば、Gender です。

7.  **可視エントリ**一覧をデコレータは表示するか、このドメイン プロパティの値を追加します。 たとえば、Male です。

8.  各アイコンに対して、手順を繰り返します。

9. **すべてのテンプレートを変換**、ビルドし実行、およびテストのダイアグラムを開きます。

10. 制御するプロパティの値を変更すると、デコレーター必要があります表示され、非表示になります。

 多くの場合、単純な一連の値よりも複雑な式によって制御されるを表示します。 たとえば、アイコンが特定の種類のリンクの数に依存しているか、かどうかに依存させる、数値は、特定の範囲内がします。 その場合は、次の手順に従います。

#### <a name="to-control-the-visibility-of-a-decorator-based-on-a-formula"></a>式に基づくデコレーターの可視性を制御するには

1.  ドメイン クラスには、計算ドメインのプロパティを追加します。 **プロパティ**ウィンドウでは、次の値を設定します。

     **IsBrowsable =**`False`**-ユーザーのプロパティを非表示にこの** 

     **種類 =**`Calculated`**-これは、その値を計算するコードを指定することは意味** 

     **名前**たとえば**DecoratorControl**

     **型** = `Boolean`

     詳細については、次を参照してください。[記憶域のカスタム プロパティして計算された](../modeling/calculated-and-custom-storage-properties.md)です。

2.  デコレーターの可視性を制御する新しいプロパティを作成します。

    1.  ドメイン クラスから灰色の線、図形にはダイアグラム要素のマップを選択します。 **DSL 詳細**ウィンドウを開いた、 **DecoratorMap**タブです。

    2.  チェック、**可視性フィルター**ボックス。

    3.  **フィルター プロパティ**、コントロールのプロパティを選択して**DecoratorControl**です。

    4.  **可視エントリ**、入力`True`です。

3.  をクリックして**すべてのテンプレートの変換**ソリューション エクスプ ローラーのツールバー。

4.  をクリックして**ソリューションのビルド**上、**ビルド**メニュー。

5.  表示されているエラー報告をダブルクリックして:"*YourClass*は定義を含んでいない GetDecoratorControlValue の..."です。

     Dsl\GeneratedCode\DomainClasses.cs では、テキスト エディターが開きます。 強調表示されたエラーの上はメソッドを追加することを要求するコメントです。

6.  不足している名前空間、クラスおよびメソッドに注意してください。  たとえば、Company.FamilyTree.Person.GetDecoratorControlValue() です。

7.  個別のコード ファイルでは、不足しているメソッドを格納する部分クラス定義を記述します。 例えば:

    ```
    namespace Company.FamilyTree
    { partial class Person
      { bool GetDecoratorControlValue()
        {
          return this.Children.Count > 0;
    } } }
    ```

     プログラム コードを使用してモデルをカスタマイズする方法の詳細については、次を参照してください。[を移動すると、プログラム コードでモデルを更新する](../modeling/navigating-and-updating-a-model-in-program-code.md)です。

8.  再構築し、ソリューションを実行します。

## <a name="see-also"></a>関連項目

- [シェイプとコネクタの定義](../modeling/defining-shapes-and-connectors.md)
- [ダイアグラムへの背景イメージの設定](../modeling/setting-a-background-image-on-a-diagram.md)
- [プログラム コードにおけるモデル内の移動およびモデルの更新](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [ドメイン固有言語をカスタマイズするコードの記述](../modeling/writing-code-to-customise-a-domain-specific-language.md)