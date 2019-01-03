---
title: アイコンまたはデコレーターの可視性の制御
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: a8fc55493aab5a19a175b75b7b1d808e9fa156e9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53877563"
---
# <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>アイコンまたはデコレーターの可視性の制御
A*デコレーター*がアイコンか、ドメイン固有言語 (DSL) 内の図形に表示されるテキストの行。 デコレーターの表示を作成でき、モデル内のプロパティの状態によって非表示になります。 など、人を表す図形、個人の性別、子供の数に応じて表示されると、さまざまなアイコンがある可能性があります。

## <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>アイコンまたはデコレーターの可視性を制御します。
 次の手順では、既に定義した図形、およびそのマッピングをドメイン クラスを前提としています。 詳細については、次を参照してください。[ドメイン固有言語を定義する方法](../modeling/how-to-define-a-domain-specific-language.md)します。

#### <a name="to-control-the-visibility-of-an-icon-or-text-decorator"></a>アイコンやテキスト デコレーターの可視性を制御するには

1. DSL 定義図では、アイコンまたは表示するテキスト デコレータ シェイプ クラスを追加します。

   1.  シェイプ クラスを右クリックし、**追加**デコレーターの必要な型を順にクリックします。

   2.  設定のデコレーターの**位置**プロパティ。 1 つ以上のデコレーターは、同じ位置を持つことができます。 たとえば、male と female の同じ位置の共有のアイコンがある可能性があります。

   3.  設定、**アイコンの既定の**アイコンのデコレーターのプロパティ。

2. 灰色の線は DSL 定義図で図形クラスと、ドメインである図要素マップを選択します。

3. DSL の詳細 ウィンドウで、**デコレーター マップ**タブで、デコレーターを選択します。 たとえば、MaleDecorator です。

4. チェック、**可視性フィルター**ボックス。

5. ドメイン プロパティの可視性を制御する必要がありますが、即時のドメイン クラスにある場合、以下のままにして**フィルター プロパティへのパス**空白。

    それ以外の場合、ドロップ ダウン メニューをクリックし、リレーションシップ、クラス、プロパティがある場所に移動します。

   -   エラー報告を回避する必要がありますいない内を移動するリレーションシップでマークされた"*"で、ナビゲーション ツール。

6. 設定、**フィルター プロパティ**ドメイン プロパティにします。 たとえば、性別です。

7. **可視性エントリ**一覧で、対象のデコレータを表示するか、このドメイン プロパティの値を追加します。 たとえば、男性です。

8. 各アイコンに対して、手順を繰り返します。

9. **すべてのテンプレートの変換**、ビルドし実行、およびテストのダイアグラムを開きます。

10. 制御するプロパティの値を変更すると、デコレーターが表示され、表示されなくなります。

    多くの場合、単純な一連の値よりもさらに複雑な式によって制御されるを表示します。 たとえば、アイコンが、特定の型のリンクの数に依存しているかどうかに依存させるまたは数値が特定の範囲内が。 その場合は、次の手順を使用します。

#### <a name="to-control-the-visibility-of-a-decorator-based-on-a-formula"></a>式に基づくデコレーターの可視性を制御するには

1.  ドメイン クラスには、計算ドメイン プロパティを追加します。 **プロパティ**ウィンドウで、次の値を設定します。

     **IsBrowsable =**`False`**-非表示に、ユーザーからのプロパティ**

     **種類 =**`Calculated`**-つまり、その値を計算するコードを指定します。**

     **名前**たとえば**DecoratorControl**

     **型** = `Boolean`

     詳細については、次を参照してください。[計算とストレージのカスタム プロパティ](../modeling/calculated-and-custom-storage-properties.md)します。

2.  デコレーターの可視性を制御する新しいプロパティを作成します。

    1.  ドメイン クラスから図形に灰色の線である図要素マップを選択します。 **DSL の詳細**ウィンドウを開いて、 **DecoratorMap**タブ。

    2.  チェック、**可視性フィルター**ボックス。

    3.  **フィルター プロパティ**、コントロールのプロパティを選択します。 **DecoratorControl**します。

    4.  **可視性エントリ**、入力`True`します。

3.  クリックして**すべてのテンプレートの変換**で、**ソリューション エクスプ ローラー**ツールバー。

4.  クリックして**ソリューションのビルド**上、**ビルド**メニュー。

5.  エラー レポートが表示されていたをダブルクリックします。"*YourClass*は定義を含んでいない GetDecoratorControlValue の..."です。

     テキスト エディターは、Dsl\GeneratedCode\DomainClasses.cs でが開きます。 上記の強調表示されたエラーは、メソッドを追加することを要求するコメントです。

6.  不足している名前空間、クラスおよびメソッドに注意してください。  たとえば、Company.FamilyTree.Person.GetDecoratorControlValue() です。

7.  別個のコード ファイルでは、存在しないメソッドを含む部分クラス定義を作成します。 例:

    ```
    namespace Company.FamilyTree
    { partial class Person
      { bool GetDecoratorControlValue()
        {
          return this.Children.Count > 0;
    } } }
    ```

     プログラム コードでモデルをカスタマイズする方法の詳細については、次を参照してください。[を移動すると、プログラム コードでのモデルを更新する](../modeling/navigating-and-updating-a-model-in-program-code.md)します。

8.  再構築し、ソリューションを実行します。

## <a name="see-also"></a>関連項目

- [シェイプとコネクタの定義](../modeling/defining-shapes-and-connectors.md)
- [ダイアグラムへの背景イメージの設定](../modeling/setting-a-background-image-on-a-diagram.md)
- [プログラム コードにおけるモデル内の移動およびモデルの更新](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [ドメイン固有言語をカスタマイズするコードの記述](../modeling/writing-code-to-customise-a-domain-specific-language.md)